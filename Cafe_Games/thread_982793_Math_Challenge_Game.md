---
title: "Math Challenge Game"
date: 2008-11-15
forum: Cafe Games
---

### Post by tom66 on 2008-11-15
Here's a math challenge for you:

You have nine coins and a balancing scale (the type which tilts depending on which object is heavier). You know that one of the nine coins is a counterfeit, and weighs slightly less than the others, which all weigh the same. Using just two weighings, how can you determine the counterfeit coin?

The person who answers this can post another challenge.

---

### Post by Diptansu on 2008-11-15
I have solved it . :) ... it was too easy.

1) At first I put 3 balls in each side of the balance.
   3 things can happen. a) Left side is lighter b) Right side is lighter c) Both side is equal. Whatever happens we can decrease our research into 3 balls only.

2) Next step is very easy. Now I have to put only 1 ball in each side. Its done. :D

---

### Post by Diptansu on 2008-11-15
Now i am gonna give you a real tough one.

There are 12 balls. One of them is of different weight (Lighter or heavier you dont know). Now you only weight 3 times on a balance as mentioned in the previous problem and detect the 'X' ball (of different weight). And you should be able to tell that it is lighter or heavier.

I only say... its real tough guys. :D

---

### Post by mali2297 on 2008-11-16
> **Diptansu said:**
> Now i am gonna give you a real tough one.

There are 12 balls. One of them is of different weight (Lighter or heavier you dont know). Now you only weight 3 times on a balance as mentioned in the previous problem and detect the 'X' ball (of different weight). And you should be able to tell that it is lighter or heavier.

I only say... its real tough guys. :D

OK, I've wasted an hour with this. Here's my somewhat messy solution.

Assign each ball a number 1,2,...,12 and perform the following two trials:

1) Weigh 1,2,3,4 against 5,6,7,8.
2) Weigh 3,4,5,6 against 8,9,10,11.

Consider the possible outcomes...

3a) If both weighings are balanced, then it's clear that the X ball is 12. 
Weigh it against ball number 1 (say) and you will now whether it weighs less 
or more.

3b) Suppose the first weighing is balanced but not the second. Then X must
be one of 9,10 or 11 and you know whether it weighs less or more. Weigh 9 
against 10 to identify it.

3c) Suppose the second weighing is balanced but not the first. Then X must
be 1,2 or 7. Weigh 1 against 2 to find the answer.

3d) Suppose both weighings are unbalanced but in different directions. Then
X is 5 or 6. Weigh 5 against 6 and you will know the answer.

3e) Finally, suppose both weighings are unbalanced in the same direction.
Then X is 3,4 or 8. Weigh 3 against 4 and you will know the answer.

---

### Post by Diptansu on 2008-11-16
YESSSS !!!! :) ... You have done it man ... Congratulation !! :)

Any wy, I myself had somewhat a different solution and at first glance as it didnt match with yours I thought you are wrong. But you are not. Then I realized my solution is almost same as yours with the following difference ...

In 2nd balance there are two balls you are changing sides. ball-5 and ball-6. Thats why in the situation as "3d)" you are having only two balls left. I myself changed 3 balls. So in that case in the situation as "3d)" i had to look among 3three balls, but as in situation like "3e)" i had 2 balls left. 

... Minor differences ... Both are correct ... :)

Now its your turn to give something for us... If you dnt have anything just tell ... may be I or somebdy else will continue ... But I am sure u hv something ... :)

---

### Post by mali2297 on 2008-11-17
This is a problem from projecteuler.net:
> 
2520 is the smallest number that can be divided by each of the numbers from 1 to 10 without any remainder.

What is the smallest number that is evenly divisible by all of the numbers from 1 to 20?

I guess it is meant as a programming challenge, but give a *paper and pen* solution.

Hint:
Every integer greater than 1 can be written as a unique product of prime numbers. For instance, 20 = 2*2*5.

---

### Post by Diptansu on 2008-11-17
If one take it like a quiz then the number is 232,792,560. If google is not wrong. But the question is to give a paper and pen solution.

I think that is too tough for me , as I am not a student of math or comp. programming or anything like that. If it was some kinda riddle may be I would have tried :p.

I think "Th3Professor" will surely give us the answer ... invite him. :)

---

### Post by cb951303 on 2008-11-17
> **Diptansu said:**
> If one take it like a quiz then the number is 232,792,560. If google is not wrong. But the question is to give a paper and pen solution.

I think that is too tough for me , as I am not a student of math or comp. programming or anything like that. If it was some kinda riddle may be I would have tried :p.

I think "Th3Professor" will surely give us the answer ... invite him. :)

found the same solution, easily solved with pen and paper

write down all the prime divisors of every number from 1 to 20. multiply the prime numbers with the highest exponential = 2^4 * 3^2 * 5 * 7 * 11 * 13 * 17 * 19

---

### Post by scragar on 2008-11-17
hmn...

we gan ignore anything that's not a prime, then multiple the highest power of each out:

1 can be ignored, even if you count it as a prime it's not gonna change the result.
[B]2's highest power is 4, which gives 16: 2*2*2*2
3's highest power is 2, so 9 : 3*3
[/B]4 can be ignored, it's just a power of 2.
[B]5 is a prime, include it: 5
[/B]6 is 2*3, ignore it.
[B]7 is prime, include it.
[/B]8 is a power of 2, ignore.
9 is a power of 3, ignore.
10 is 5*2, ignore.
[B]11 is prime, include it.
[/B]12 is 2*2*3, ignore it
[B]13, prime, include
[/B]14 is 7*2, ignore
15 is 5*3, ignore
16 = power of 2, ignore
**17 is prime.**
18 = 3*3*2, ignore
**19 is prime**
20 is 2*2*5

so in the end we've got:

2*2*2*2*3*3*5*7*11*13*17*19 == 232,792,560



EDIT: poopy, cb951303  got there before me.

---

### Post by Diptansu on 2008-11-17
Silly me :p ... I didnt even try thinking it would be too tough for me ...lol :p

Well I think now cb951303 or scragar should post somthing interesting ... for others to think ... :)

---

### Post by scragar on 2008-11-17
I'll give it 20 minutes and if cb951303 hasn't come up with something I'll post a puzzle.

---

### Post by Diptansu on 2008-11-17
Okay ... but where is tom66, who originally created the thread. We r missing him ... :)

---

### Post by cb951303 on 2008-11-17
> **scragar said:**
> I'll give it 20 minutes and if cb951303 hasn't come up with something I'll post a puzzle.

please do so, I don't have anything in mind :)

---

### Post by scragar on 2008-11-17
No idea where tom66 is, he's not posted since the thread was made, maybe he went to bed or something.


ok, 4 people are to cross a bridge at night which only 2 people can be on at once, given that they only have 1 torch, the light of which covers 1/3 of the bridge in a single direction(from the person holding it) and it takes each person the respective amount of time to cross the bridge:

Alice - 1 minute
Bob - 2 minutes
Charles - 4 minutes
Dora - 8 minutes

What is the fastest method for them to all cross the bridge?

Please ask questions if I'm confusing or havn't made it clear, it's just a deviation of the classic puzzle made a bit harder thanks to the lights range(which is previously considered to be negligable)

---

### Post by Diptansu on 2008-11-17
I hope I have solved this one ... but scragar should check once...

Before I start explaining lets divide the bridge into three segments. It looks like this ...

----------1/3-----------2/3-----------

now each segments can be lighten at one time and at a single direction. Suppose all are crossing the bridge from left to right.

Now,

1)To start with, Dora and Alice will cross at first. Surly Dora will hold the torch and never stop in between. (I thought about it because they need at least 8 min. as Dora cant go faster. Now someone should bring back the torch and I think Alice is most suitable for the job as she will need least time.) 
So, Dora will not stop in between, but Alice will. At first Alice will stop at the 1/3 rd point and wait for Dora to come. After Dora reach the 1/3 rd point Alice will start towards the 2/3rd point and again wait for Dora to reach. I repeat, Dora will never stop in between. After she reach the 2/3 rd point, she will handover the torch to Alice, and Alice, standing at the 2/3rd point, show Dora light in that direction until she reach the other end.
2) As soon as Dora reach the other end, Alive will come to the 1/3rd point and point the torch towards the left end. Now Its Charles time to cross. As in the previous case, Charles too will not stop at anywhere in between, and take the torch from Alice at 1/3 rd point. Then they both start moving. Alice reach the 2/3rd point earlier and wait for Charles to give her the torch again. then she point it towards the right end from the 2/3rd point. and Charles crosses the bridge.
3) Now again she comes to the 1/3rd point, without wasting any time after Charles reach the other end. Now Bob starts. And obviously doesnt stop in between and thus both Alice and Bob cross the bridge in 2 mins, not to say Alice waited for him at 1/3rd and 2/3rd points to have sufficient light for her to cross.

TIME CALCULATION:

Dora crosses in 8 minutes.
Charles in 4 mins.
Bob in 2.
Alice two times cover the distance between 1/3rd point and 2/3rd point. So she takes 2/3 minutes.
So they crosses the bridge in 14+2/3 minutes.

I dont know i missed something or not. If you guys think that I am right, i am ready to post my next puzzle. :)

---

### Post by scragar on 2008-11-17
> **Diptansu said:**
> I hope I have solved this one ... but scragar should check once...

Before I start explaining lets divide the bridge into three segments. It looks like this ...

----------1/3-----------2/3-----------

now each segments can be lighten at one time and at a single direction. Suppose all are crossing the bridge from left to right.

Now,

1)To start with, Dora and Alice will cross at first. Surly Dora will hold the torch and never stop in between. (I thought about it because they need at least 8 min. as Dora cant go faster. Now someone should bring back the torch and I think Alice is most suitable for the job as she will need least time.) 
So, Dora will not stop in between, but Alice will. At first Alice will stop at the 1/3 rd point and wait for Dora to come. After Dora reach the 1/3 rd point Alice will start towards the 2/3rd point and again wait for Dora to reach. I repeat, Dora will never stop in between. After she reach the 2/3 rd point, she will handover the torch to Alice, and Alice, standing at the 2/3rd point, show Dora light in that direction until she reach the other end.
2) As soon as Dora reach the other end, Alive will come to the 1/3rd point and point the torch towards the left end. Now Its Charles time to cross. As in the previous case, Charles too will not stop at anywhere in between, and take the torch from Alice at 1/3 rd point. Then they both start moving. Alice reach the 2/3rd point earlier and wait for Charles to give her the torch again. then she point it towards the right end from the 2/3rd point. and Charles crosses the bridge.
3) Now again she comes to the 1/3rd point, without wasting any time after Charles reach the other end. Now Bob starts. And obviously doesnt stop in between and thus both Alice and Bob cross the bridge in 2 mins, not to say Alice waited for him at 1/3rd and 2/3rd points to have sufficient light for her to cross.

TIME CALCULATION:

Dora crosses in 8 minutes.
Charles in 4 mins.
Bob in 2.
Alice two times cover the distance between 1/3rd point and 2/3rd point. So she takes 2/3 minutes.
So they crosses the bridge in 14+2/3 minutes.

I dont know i missed something or not. If you guys think that I am right, i am ready to post my next puzzle. :)

That's not an optimal solution, it's an easy one, but it's not the quickest, which I was asking for(I can think of a way to shave over a minute)

EDIT: corrected last statement, I was miss judging something :P

---

### Post by Diptansu on 2008-11-17
Okay ... thanks for your quick reply ... Lemme try again ... I think people out here will surely get into the solution soon even if I fail :p ...So wait ... :)

---

### Post by scragar on 2008-11-17
OK, I've got stuff to do, so here's a simple idea, the absolute solution requires you to work in a 1/15th of the bridge, but if you get close without it(2 solutions, same time for both), which is only 40 seconds off the optimal then I guess it counts.

The MD5 for the two matching solutions is: **af63108d82ab5ae750ac60f68b500496**
And for the absolute optimal(which takes a fair bit more working out): **882b0b1c72049ea323528b27af4dd8bf**
[http://hash-it.net/](http://hash-it.net/)

I know it's possible to brute force these pretty quickly, so use them for checking ONLY, I want an explination behind the time anyway :P

---

### Post by mali2297 on 2008-11-17
I guess that I haven't found the optimal solution but I can beat Diptansu's time with 40 seconds.

1) Let Charles and Dora walk first. Charles stops at position 2/3 holding the torch as Dora walks over to the other side. This takes 8 minutes.

2) Charles walks back to position 1/3 which takes 4/3 minutes.

3) Bob and Charles begin to walk towards the other end. When Charles reaches position 2/3, Bob has catched up. Bob takes over the torch and let Charles go the last distance alone. This stage takes 4 * 2/3 = 8/3 minutes.

4) Bob goes back to position 1/3 in 2/3 minutes.

5) Finally, Bob walks to the other end with Alice catching up behind him. This takes 2 * 2/3 = 4/3 minutes.

In total: 8 + 4/3 + 8/3 + 2/3 + 4/3 = 14 minutes.

---

### Post by scragar on 2008-11-17
> **mali2297 said:**
> I guess that I haven't found the optimal solution but I can beat Diptansu's time with 40 seconds.

1) Let Charles and Dora walk first. Charles stops at position 2/3 holding the torch as Dora walks over to the other side. This takes 8 minutes.

2) Charles walks back to position 1/3 which takes 4/3 minutes.

3) Bob and Charles begin to walk towards the other end. When Charles reaches position 2/3, Bob has catched up. Bob takes over the torch and let Charles go the last distance alone. This stage takes 4 * 2/3 = 8/3 minutes.

4) Bob goes back to position 1/3 in 2/3 minutes.

5) Finally, Bob walks to the other end with Alice catching up behind him. This takes 2 * 2/3 = 4/3 minutes.

In total: 8 + 4/3 + 8/3 + 2/3 + 4/3 = 14 minutes.

ooh, now if you could just swap that order around just a little, you're so very close(and you have the right idea, letting the slowest 2 walk together).

Oh, and those MD5 hashes for checking the time are mm:ss for minutes:seconds, just thought I'd add that, given the number of possible interpretations.

---

### Post by Diptansu on 2008-11-17
I cant understand Number 3) by mali2297.
> 3) Bob and Charles begin to walk towards the other end. When Charles reaches position 2/3, Bob has catched up. Bob takes over the torch and let Charles go the last distance alone. This stage takes 4 * 2/3 = 8/3 minutes.


Now Bob was at the starting point and Charles was at 1/3rd point. Now if both starts at the same time towards the other end in which direction the torch was pointed? 
* If Charles points it towards the starting point to help Bob to come, he himself cant move until Bob catches him at 1/3rd point and they start at same speed or Chrles hold the torch. 
* If Charles points it towards the end point, how on earth Bob take his first step on the bridge as the torch is pointed towards the other end.

It also true for his No. 5)
> 5) Finally, Bob walks to the other end with Alice catching up behind him.

In here, nobody can 'catch' other 'from behind' as he wont get the light.

I am probably coming soon with a new Idea to solve this. :p

---

### Post by mali2297 on 2008-11-18
> **Diptansu said:**
> 
* If Charles points it towards the starting point to help Bob to come, he himself cant move until Bob catches him at 1/3rd point and they start at same speed or Charles hold the torch.


I see; it's a valid point. I didn't know that the person needs to point the torch in the direction he/she walks.

We have interpreted the rules differently. Perhaps scragar can come with a clarification.

---

### Post by scragar on 2008-11-18
> 1) Let Charles and Dora walk first. Charles stops at position 2/3 holding the torch as Dora walks over to the other side. This takes 8 minutes.
```
Start		1/3		2/3		End
AB				C		D
```

> 2) Charles walks back to position 1/3 which takes 4/3 minutes.
```

Start		1/3		2/3		End
AB		C				D
```


> 3) Bob and Charles begin to walk towards the other end. When Charles reaches position 2/3, Bob has catched up. Bob takes over the torch and let Charles go the last distance alone. This stage takes 4 * 2/3 = 8/3 minutes.

```

Start		1/3		2/3		End
A				BC		D	--- B walks twice as fast as C
A				B		CD
```


> 4) Bob goes back to position 1/3 in 2/3 minutes.

```

Start		1/3		2/3		End
A		B				CD
```


> 5) Finally, Bob walks to the other end with Alice catching up behind him. This takes 2 * 2/3 = 4/3 minutes.
```

Start		1/3		2/3		End
				AB		D	--- A walks twice as fast as B
						ABCD
```
I think we need to have some more set rules over who's holding the torch, maybe put an * after their name, or underline/bold it so we can tell it appart.

---

### Post by Diptansu on 2008-11-18
Okay I still have a solution ... Which gives the same time as mali2297 ... Here it is.

The basic concept of this solution is if a person with lower speed holds the torch and start to walk towards the end while another person with greater speed is moving ahead of him, the person ahead cannot increase the distance between him and the torch holder more than 1/3rd of the bridge. Otherwise the person moving ahead will go beyond the range of the torch and thus cant see anything. As soon as the distance between them become 1/3rd they will start to move at the same speed (certainly the person with greater speed will decrease his speed and make it equal with the person behind.)

Now, as for the solution, though not the optimal one, but kind of corrected version of mali ...

1) Alice and Bob start to move at the same time while Bob holding the torch. After **[SIZE="3"]2/3 mins[/SIZE]** Alice reach 2/3 rd point and Bob reach 1/3rd point. The distance between them is 1/3rd (of The Bridge), so Alice cannot continue at her normal speed any more. From now on she moves at Bob's speed and thus she doesnt go beyond the range of the torch. Thus she reach the other end and Bob reach the 2/3rd point at **[SIZE="3"]2/3 mins[/SIZE]**. Then again, after Alice reached the other end Bob come back to the 1/3rd point. It again takes **[SIZE="3"]2/3 mins[/SIZE]**. 

So Time Taken = 3 * 2/3 mins = 2 mins.

2) Then Charles starts. He meets with bob at 1/3rd point after **[SIZE="3"]4/3 mins[/SIZE]**. As soon as he reach the 1/3rd point, Bob give him the torch and they both start to walk towards the end. After **[SIZE="3"]4/3 mins[/SIZE]** bob reach the other end and Charles reach the 2/3rd point. Point to be noticed never there distance gone beyond the 1/3rd of the bridge. Then again Charles come back to the 1/3rd point in **[SIZE="3"]4/3 mins[/SIZE]**.

So Time Taken = 3 * 4/3 mins = 4 mins.

3) At last Dora starts. She came to 1/3rd point in **[SIZE="3"]8/3 mins[/SIZE]**. Then both Dora and Charles start towards the end at there normal speed from the 1/3rd point and Dora reach there after **[SIZE="3"]16/3 mins[/SIZE]** obviously.

So Time Taken = (8/3 + 16/3) mins = 8 mins.

So total time needed is ... 2+4+8= 14 mins.

this is same as calculated by mali, but keeping in mind the direction of the torch. 

By the way ... 
> The MD5 for the two matching solutions is: af63108d82ab5ae750ac60f68b500496
And for the absolute optimal(which takes a fair bit more working out): 882b0b1c72049ea323528b27af4dd8bf
[http://hash-it.net/](http://hash-it.net/)


i didnt understand what they mean. :p

---

### Post by Diptansu on 2008-11-18
scragar didnt say anything (at #23) about the torch direction problem what i have mentioned in post #21. :o

---

### Post by scragar on 2008-11-18
> i didnt understand what they mean. 
Meh, doesn't matter, 13minutes 20seconds is the best time I could get, then with a lot of messing about, and calculating 1/15th's of the bridge etc I was able to shave another 40 seconds from this time. That is, as far as I know, the absolute optimized solution.

As I said though, mali2297's solution is very close, if you just change the orders around and make a couple of extra trips you can get down to my initial solution(there are 2, both giving the exact same time), just think about why (s)he has the slowest people making extra trips.

---

### Post by scragar on 2008-11-18
> **Diptansu said:**
> scragar didnt say anything (at #23) about the torch direction problem what i have mentioned in post #21. :o


I never really thought about the torch direction problem, I assumed that the torch cannot be pointed behind someone while they walk(kinda removes from it's purpose then :P), but if people took it to mean that 2 people can never be more than 1/3 of the bridge apart, well I think, given the optimum solutions, that it makes a fairly negligible amount of difference, so either way it doesn't make a large difference in final time.

---

### Post by Diptansu on 2008-11-18
Okay surly i will think about it , but there is a problem about the rule of holding the torch. If it is not possible to cross the bridge without the torch pointing to that direction, Number 3) and Number 5) in mali's solution (#19) is impossible.

Is it so, or I am miss interpreting something?

---

### Post by scragar on 2008-11-18
> **Diptansu said:**
> Okay surly i will think about it , but there is a problem about the rule of holding the torch. If it is not possible to cross the bridge without the torch pointing to that direction, Number 3) and Number 5) in mali's solution (#19) is impossible.

Is it so, or I am miss interpreting something?

As I said, I never actually specified when I made the puzzle how that should be handled, so if someone was to miss understand it's not exactly their fault. The solutions I gave generated do rely on the idea of people being able to see where they are walking, so those are the solutions I will be looking for.

If no-one has got a better solution within 24 hours though, I'm calling it quits and declaring someone the winner, I'm too busy to keep commenting on the puzzle.

---

### Post by Diptansu on 2008-11-18
> I'm too busy to keep commenting on the puzzle.

I am sorry if I have disturbed u, but i didnt want you to comment at that very moment i posted my question. I thought u will answer when u get enough time. :)

> The solutions I gave generated do rely on the idea of people being able to see where they are walking

I still dont understand why they need a torch then if they can see without it. Anyway, I am still confused and I quit. :p

> If no-one has got a better solution within 24 hours though, I'm calling it quits and declaring someone the winner

I think people out here are more willing to know your solution than to know who is the winner. :)

---

### Post by mali2297 on 2008-11-18
> **Diptansu said:**
> Okay I still have a solution ... Which gives the same time as mali2297 ... Here it is.

The basic concept of this solution is if a person with lower speed holds the torch and start to walk towards the end while another person with greater speed is moving ahead of him, the person ahead cannot increase the distance between him and the torch holder more than 1/3rd of the bridge. Otherwise the person moving ahead will go beyond the range of the torch and thus cant see anything. As soon as the distance between them become 1/3rd they will start to move at the same speed (certainly the person with greater speed will decrease his speed and make it equal with the person behind.)

Now, as for the solution, though not the optimal one, but kind of corrected version of mali ...

1) Alice and Bob start to move at the same time while Bob holding the torch. After **[SIZE="3"]2/3 mins[/SIZE]** Alice reach 2/3 rd point and Bob reach 1/3rd point. The distance between them is 1/3rd (of The Bridge), so Alice cannot continue at her normal speed any more. From now on she moves at Bob's speed and thus she doesnt go beyond the range of the torch. Thus she reach the other end and Bob reach the 2/3rd point at **[SIZE="3"]2/3 mins[/SIZE]**. Then again, after Alice reached the other end Bob come back to the 1/3rd point. It again takes **[SIZE="3"]2/3 mins[/SIZE]**. 

So Time Taken = 3 * 2/3 mins = 2 mins.

2) Then Charles starts. He meets with bob at 1/3rd point after **[SIZE="3"]4/3 mins[/SIZE]**. As soon as he reach the 1/3rd point, Bob give him the torch and they both start to walk towards the end. After **[SIZE="3"]4/3 mins[/SIZE]** bob reach the other end and Charles reach the 2/3rd point. Point to be noticed never there distance gone beyond the 1/3rd of the bridge. Then again Charles come back to the 1/3rd point in **[SIZE="3"]4/3 mins[/SIZE]**.

So Time Taken = 3 * 4/3 mins = 4 mins.

3) At last Dora starts. She came to 1/3rd point in **[SIZE="3"]8/3 mins[/SIZE]**. Then both Dora and Charles start towards the end at there normal speed from the 1/3rd point and Dora reach there after **[SIZE="3"]16/3 mins[/SIZE]** obviously.

So Time Taken = (8/3 + 16/3) mins = 8 mins.

So total time needed is ... 2+4+8= 14 mins.

this is same as calculated by mali, but keeping in mind the direction of the torch. 


I don't think I will be able to find a better solution than the above. Instead, I will await scragar to post the "answer".

---

### Post by scragar on 2008-11-18
OK, Diptansu came up with the fastest solution that actually works with the torch, so I guess he wins.
```

Total	step	Start		1/3		2/3		end
00:00	0:00	ABCD
00:40	0:40	CD		A**B**
01:20	0:40	CD				**B**		A
02:40	0:40	**B**CD
10:40	8:00	B						A**CD**
11:20	0:40	B		**A**				CD
12:00	0:40			A**B**				CD
13:20	1:20							A**B**CD

```
As you can see, it's a faster solution just be re-ording the people and making A and B do all the running back and forth. You can cut a bit of time out of this, not much in a single action, but 8 seconds here, 20 seconds there adds up to 40 seconds from the total time.

```

Total	step	Start	*1/15*	*2/15*	1/3		2/3		end
00:00	0:00	ABCD
00:40	0:40	CD			A**B**
01:20	0:40	CD					**B**		A
------------------------- same up till here
02:00	0:40	CD			**B**				A
02:32	0:32	C	**B**D						A
02:40	0:08	BC	**D**						A
03:44	1:04	B		**C**D					A
10:40	6:56	B							A**C**D
------------------------- that's already 40 seconds off the end time

```I kinda didn't notice that you could shave a bit more time off here as well, if D holds the torch and waits for C to reach the end, A can meet D a fraction further along, then hold the torch while D walks back to the end, this saves a bit of time, just not much, still, it's 8 seconds you could spend doing something else :P

So anyway, Diptansu, You're up.

---

### Post by Diptansu on 2008-11-18
Here scragar gave two solutions. I am still thinking about the 2nd solution he gave. So I am still not in a position to comment on that ... But I have a question about his first solution. 

```

Total	step	Start		1/3		2/3		end
00:00	0:00	ABCD
00:40	0:40	CD		AB
01:20	0:40	CD				B		A
02:40	0:40	BCD
10:40	8:00	B						ACD
11:20	0:40	B		A				CD
12:00	0:40			AB				CD
13:20	1:20						        ABCD

```
This is what he wrote. So in the 3 rd step, 'B' is at the 2/3rd point while at the 4th step he is at the starting point. And for covering this distance only 40 sec he took !!! ...

Am i missing something?

---

### Post by cb951303 on 2008-11-18
> **Diptansu said:**
> Here scragar gave two solutions. I am still thinking about the 2nd solution he gave. So I am still not in a position to comment on that ... But I have a question about his first solution. 

```

Total	step	Start		1/3		2/3		end
00:00	0:00	ABCD
00:40	0:40	CD		AB
01:20	0:40	CD				B		A
02:40	0:40	BCD
10:40	8:00	B						ACD
11:20	0:40	B		A				CD
12:00	0:40			AB				CD
13:20	1:20						        ABCD

```
This is what he wrote. So in the 3 rd step, 'B' is at the 2/3rd point while at the 4th step he is at the starting point. And for covering this distance only 40 sec he took !!! ...

Am i missing something?

yeah it looks like 80 secs to me, the total time is correct though. it's a typo i think

---

### Post by Diptansu on 2008-11-18
Sorry. I think it was my mistake. In total time you added it right ... But in the 'step' column i think its not correctly written ... But anyway, It was a nice solution, I am a fool that didnt get that ... :p 

Lets take a look at his next sol. :)

---

### Post by scragar on 2008-11-18
Yeah, that's my fault, I was coping it from a text document in a not very easy to follow format into that one so I could explain it better, I made a bit of a mistake with that.

Anyway, your puzzle Diptansu

---

### Post by Diptansu on 2008-11-18
I have another humble question to scragar ... (lol, I dnt know its a really silly one or not ... :p) ... anyway, I am a brave silly ... :p

In both of your solution, after 10:40 mins passed, the situation is same.

Then why this complicated 2nd solution? 

I think I am again missing something .:p

---

### Post by scragar on 2008-11-18
again, my fault, it's quicker, I've just added it up wrong when I was coping it from one format to the other(a lot harder to add up to 60 than you think when you start adding strange little fractions).

---

### Post by Diptansu on 2008-11-18
> again, my fault, it's quicker, I've just added it up wrong

I still cant understand on which step did you make the mistake in adding in the 2nd solution? ... Mention it please ... (I think I am becoming dumber gradually :p)

---

### Post by Diptansu on 2008-11-20
Days passed. nobody answered my question. :( (Was it too silly ...?)

Anyway, to make this thread alive, I am going to post another puzzle. (Though I dont think myself a 'winner' as scragar said. I didnt get that brilliant 13 M 20 S solution of his.)

The Puzzle:

A party is about to be held within 2 days on Duke's honor. 1000 bottle of wine has been ordered for the occasion. But suddenly intelligence got informed that 1 of those bottles has been poisoned. So 10 dogs are arranged to test. But the problem is, the poison takes exactly 2 days to show any symptom, and that is sudden death. So, its only one time those bottles can be tested on the dogs, and have to identify the poisoned bottle just after getting the result (poor dogs). One dog can drink from more than one bottle. and which dog drinking from how many bottles can be notified.

Just tell what could be the procedure two identify a poisoned bottle among those 1000, using the dogs, within 2 days, when poison react just after 2 days and react suddenly.

If anybody have any question to clarify the problem even more, ask me. 

:)

---

### Post by scragar on 2008-11-20
Oh, I'm sorry, I'm subscribed to the thread, I just check my emails from time to time for new links, I never recived the last email for this thread though. I've deleted the text file my little program output though, so I don't know where it went wrong, I've forgotten about it(there's a good reason I use email reminders, I've got a terrible memory).

I've seen that problem before, it's based on 1,000 being very close to 1,024, which just so happens to be the size of 10 bytes. so each bottle get's labeled in binary:
```
bottle   1  00 00 00 00 01
bottle  2  00 00 00 00 10
...
bottle 999 11 11 10 01 11
```
when the dogs die from the poison you know the binary for the bottle, and can get rid of it(bottle 1,000 doesn't even need testing).

PS: I'm too good at these puzzles :P sorry.

---

### Post by Diptansu on 2008-11-20
> PS: I'm too good at these puzzles :P sorry.

I dont know why you are being 'sorry' man. 

But if u hv seen the problem beforehand u shouldnt have disclose the answer of it. People out there may accuse you killing their fun of thinking. 

Anyway, I think you sd post a new one. :)

---

### Post by scragar on 2008-11-20
I said I saw it before, I solved it myself, that was really too easy though.

I shouldn't have ruined it really. Sorry about that.

I can't think of a problem just yet, I'll think one up soon.

---

### Post by pp. on 2008-11-20
> **Diptansu said:**
> I dont know why you are being 'sorry' man. 

But if u hv seen the problem beforehand u shouldnt have disclose the answer of it. People out there may accuse you killing their fun of thinking. 

Anyway, I think you sd post a new one. :)

pls us mr lttrs.

---

### Post by Idefix82 on 2008-11-20
While you guys are thinking, I can give you a couple of puzzles if you want.

The first one is: 100 dwarves are caught by a witch. They are told that in a minute they will be positioned in a row, each dwarf facing the ones in front of him but not able to see the ones behind him. They will each get a hat, which will be either red or blue. So the one furthest in the back will be able to see the colours of the hats in front of him, the one up front will not see any colour and the others will be in between. No dwarf will see his own hat. Then starting with the dwarf in the back (who can see all the hats in front of him) and proceeding in order each dwarf will guess the colour of his hat. If he is right, he gets immediately released, otherwise he gets immediately put behind a windows machine for the rest of his life (I know this version is almost too cruel to be told to children).

The dwarves have one minute to think of a strategy before the fun begins. Once they are all placed and have their hats on, they are not allowed to say anything but "red" or "blue" and strictly in the order from the back to the front. How many dwarves can be saved and how?

Obviously, if you know the answer then keep quiet!

---

### Post by pp. on 2008-11-20
> **Idefix82 said:**
> How many dwarves can be saved and how?

Fifty or more. The hindmost dwarf counts the number of red and blue hats and says the colour which occurs more often. Every other dwarf just names the same colour.

---

### Post by Idefix82 on 2008-11-20
> **pp. said:**
> Fifty or more. The hindmost dwarf counts the number of red and blue hats and says the colour which occurs more often. Every other dwarf just names the same colour.

Yes, scragar has also offered that via PM. So 50 is the first benchmark to beat. And I assure you that it can be beaten.

---

### Post by pp. on 2008-11-22
Queries:

Do the dwarfs hear the guesses of those behind them?
If so, do they learn whether those guesses were correct?

Trivial solution:
Each dwarf who stands behind another one exchanges his cap with the one in front of him. All but the frontmost one now know the colours of their caps. Success rate 99% unless some of the dwarfs are colour blind.

---

### Post by Idefix82 on 2008-11-22
> **pp. said:**
> 
Do the dwarfs hear the guesses of those behind them?
If so, do they learn whether those guesses were correct?


Yes to both questions.
The dwarves are obviously not allowed to touch their caps, otherwise they could just take it off, look at it and put it back on. They are not allowed to use sign language, cough, throw pieces of paper through the air,... Basically no funny business.

---

### Post by mali2297 on 2008-11-22
I've got a method that I believe will save at least 99 dwarves with 
certainty. To not spoil it for the others, I've made the answer invisible. ;-)

[color=white]
EDIT: The answer is deleted.
[/color]

---

### Post by scragar on 2008-11-22
I can't believe I never thought of that, good idea mali2297. I can't imagine a better method.

---

### Post by Idefix82 on 2008-11-22
Well done!
You could delete it, in case others want to think about it but can't resist the temptation. It's completely correct, though and will be rewarded with a "thank you" :)
I think I will open my own thread with some trickier puzzles if people want me to. I could post the link to it here. Let me know if there is demand.
Edit: Just realised that I can't thank here, sorry :(

---

### Post by scragar on 2008-11-22
Oh, can I make a request for future "invisible" posts, because my BG colour here isn't white(I've found a really nice cream colour that works well with the layout and isn't nearly as harsh on the eyes) I can sort of read the invisible stuff without much trouble without needing to highlight it. This is completely negated with [code] or [quote] tags, both of which let you change the colour in them(and they don't inherit my background colour). Just saying.

---

### Post by pp. on 2008-11-22
Good job, Martin, and congratulations.

---

