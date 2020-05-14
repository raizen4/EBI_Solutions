# Notes
Due to the limited time given and the fact that I had to do in parallel 2 more technical tests, I have unfortunately not been able to code the solutions for these problems. To show you how I architect my code, what technologies I use and the industry best practices that I follow, I will include here an extra piece of work I have done in the way of a website for reading news (on github)

# Link to project showcase here: https://github.com/raizen4/TouchSystemsSubmission


# Problem 1: Space Station
## Part 1 a)
This problem relates to optimising the time needed to get all five astronouts from one point to the other in 21 minutes without letting anybody behind or in transit after the time is up.

There has been an accident on the ISS and we know that it has been split in 2. One part is losing oxygen at an alarmant rate and has 21 minutes until the staff will die. The staff is made of 5 astronauts that need to escape to the other platform.

There are only two suits available and 2 astronauts must go each time to the next platform such that one can go back with a spare space suit.

Each astronaut has his/her own speed of traveling and if an astronaut that is faster goes with one that is slower, the faster astronaut needs to wait for the slower one (think of them holding hands)

We assume that in the time required for each astronaut to make the jurney from platform A to platform B we include the time needed to put the space suit on/take it off and the negotiating of the air lock.

We cannot throw space suits from one platform to another and we are not allowed to have anybody in transit after the 21st minute.

## Part 1 b)
Given that in the example provided the fastest way of travelling is shown with Neil being the one that helps others travel to the next platform (as he is the fastest who can come back from there), I cannot see a better solution to this problem without making some assumptions. This is because we know that we only have 2 available suits and 2 astronauts must go each time to the next platform without having the possibiliy to pass back somehow the space suits in transit.

In the inital assumptions, there is said that the traveling time includes the negotiating the air lock and changing space suit. If we assume that we do not need to negotiate the air lock (say we led them both enter at the same time provided there is enough space) we might save let's say 15 seconds for each time two astronauts go in the air lock. This means that each time Neil comes with another astronaut he will get 30 seconds as they won't have to negotiate the airlock. Neil goes back 4 times to help his friends to make the jurney, so 30*4 =120 seconds which is exactly the time needed to make the whole mission succed.


# Problem 2: Tech Dungeon
## Part 1 a)
This is a decisional problem. Our main character Zara is asked to solve a challange and escape the dungeon. She carries an audio transmitter so we can hear what is going on such that we can as well escape. To escape, she needs to guess correctly the combinations to the door exit. There are a lot of these doors and she knows the hallway she went in but we don't. We need to find out based on what we hear.

She is told some very important rules.
 ### -The code has 3 number that can be from 0-99
 ### -Second number is greater or equal than the first
 ### -Third number is grater or equal than the second
 ### -She can ask only 3 clues, if she makes a wrong guess she will fail the challange.

## Part 1 b)
The problem represented here is basically reduced to the number of combinations you have after being given the first two clues. The third clue is only needed when we have more than 1 combination that gives the same answer.
Let's begin:
### First clue:  the product of the three numbers is 36. Lets generate all the possible combinations beginning with 1:
1 * 1 * 36 </br>
1 * 2 * 18</br>
1 * 3 * 12</br>
1 * 4 * 9</br>
1 * 6 * 6 </br>
2 * 2 * 9 </br>
2 * 3 * 6</br>
3 * 3 * 4</br>

### Second clue : The sum of the number is equal to the number of the hallway she entered. So let's calculate the sums now:
38</br>
21</br>
16</br>
14</br>
13</br>
13</br>
11</br>
10</br>

Now, the problem says she waited a bit and thought about something. This could happen ONLY because there must be a sum between these sums that repeats itself and that is 13. So we know she went to the hallway number 13 now. And then she asks for the last, deciding clue where she is said that the largest number appears only once in the combination. 

So the answer is : 2 * 2 * 9

# Problem 3: The cursed Temple
## Part 1 a)

This is a decisional problem with an optimization aspect because we must make sure the groups we create are optimized such that the liars cannot win. We are told we are in a cursed temple that is collapsing in no more than 1 hour. There are 4 paths to explore and 9 individuals. We know that from these 9, 2 of them lie sometimes but we do not know who and we cannot find out. The group leader cannot be the liar.

We are being told then that it takes 20 minutes to go one path. We are also told that if we are to go on all paths at once it would take 40 minutes (20- each way) to get back which will leave us exactly 20 minutes to get out on the correct way. The whole objective is to make sure that the liars do not win and the grop does not perish.

## Part 1 b)
This problem is an optimization problem in the aspect that we need to somehow make sure that the way we are splitting groups will not let the liars win. There are a lot of options in which we can break the group to go on the 4 paths we could take. For the sake of simplicity, I decided that the group leader should take a path just him as we know he is not a liar. So we have 3 paths and 8 people to assign to these paths. 

In deciding how to get the best combination, I have taken some assumptions and made some rules.

Rules and assumptions:

1) No matter how I make the groups, at any time the majority in a group must not be liars. HOWEVER, if there is a case where the majority could be liars in a group, the other 2 groups MUST have more than 2 members to win by majority (as we do not know who is lying). In this case, taking that path would be only natural, as we know that the other 2 groups are not lying and the group leader is not lying and they are the only ones that argue if that path is an exit or not.

2) The group leader must go alone on one path to take one path out of the ecuation as we know he will not be lying.

3) We assume that the 2 liars will be suicidal and don't care if the whole temple falls on them so they will lie in any case. If at least one of them would be by any means guaranteed to say the truth because of the circumstances, the problem would be very easy.

Now, given the aforementioned, the combination I have come in mind with after trial and error is the following:

3-4-1
- Lets take this one first.
- If there are 2 liars in the first group, one of them will be telling the truth so they will argue. The other 2 groups and the group leader will all say the truth and won't argue. This means that the correct path will be on the group that argues. This happens when the 2 liars are in the group of 4 as well as there will be 2 who would tell the truth whilst the other groups will have an agreed opinion.
- If there is 1 liar in the first group, and 1 in the second, the majority wins.
- If there is 1 liar in either the first or second group and 1 liar in the third group, majority wins in the first group ( so there is not chance of that group lying) whilst if the 1 guy that went alone lies, we will eliminate the other paths as we know all the other groups are saying the truth.
