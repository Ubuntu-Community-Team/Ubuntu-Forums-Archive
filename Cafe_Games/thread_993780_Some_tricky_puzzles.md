---
title: "Some tricky puzzles"
date: 2008-11-26
forum: Cafe Games
---

### Post by Idefix82 on 2008-11-26
I would like to start a little game: I will set logic puzzles and you try to solve them. The winners get a "Thank you" as a prize. Now for the rules:
[LIST=1]
[*]You must not have seen the puzzle before.
[*]You must have solved it yourself, without referring to friends, books, internet, etc.
[*]Once you think you have solved it, please send me a private message. I might then either ask you to post your solution or to wait a little.
[*]I will try to set riddles which have one optimal solution, but several intermediate ones. Please don't be shy to propose a solution even if you don't think that it's final.
[*]You can ask questions here if you need me to clarify a puzzle.
[/LIST]
Ok, in the next post the first puzzle comes:

---

### Post by Idefix82 on 2008-11-26
100 dwarves are caught by a witch. They are told that in a minute they will be positioned in a row, each dwarf facing the ones in front of him but not able to see the ones behind him. They will each get a hat, which will be either red or blue. So the one furthest in the back will be able to see the colours of the hats in front of him, the one up front will not see any colour and the others will be in between. No dwarf will see his own hat. Then starting with the dwarf in the back (who can see all the hats in front of him) and proceeding in order each dwarf will guess the colour of his hat. If he is right, he gets immediately released, otherwise he gets immediately put behind a windows machine for the rest of his life (I know this version is almost too cruel to be told to children).

The dwarves have one minute to think of a strategy before the fun begins. Once they are all placed and have their hats on, they are not allowed to say anything but "red" or "blue" and strictly in the order from the back to the front. How many dwarves can be saved and how?

Of course, the dwarves are not allowed to send any signals like coughing, throwing pieces of paper, touching each other or any of that sort. The only means of conveying information is to make a guess that everybody can hear.

---

### Post by kernelhaxor on 2008-11-26
At least half of them can be saved by doing:
Every alternate person in the row yells the color of the hat of the person immediately in front of him so that the person can repeat it and be saved.

The rest half would hav 50% chances as their hat could be either red or blue.

So on an average, 75% of the dwarfs can be saved.
Best case: All are saved.
Worst case: Only half of them are saved.

---

### Post by Idefix82 on 2008-11-26
That's a nice first attempt. Needless to say that the witch will overhear the discussion and will try to play against the agreed strategy. In other words: the worst case scenario is the criterion by which a strategy is evaluated.

Now see if you can turn 50% into 2/3.

---

### Post by kernelhaxor on 2008-11-26
Ah got it.  
Assume: 1st person is standing behind 2nd person and 2nd person is standing behind 3rd person.
1st person says 'red' if the 2nd and 3rd persons' hats are of the same color and 'blue' otherwise.  So now the 2nd person can observe the hat of the 3rd person and would know his own color as he heard what the 1st person said.  Repeat this for every third person in the row.

Worst case: 2/3

---

### Post by Idefix82 on 2008-11-26
Excellent! And now the final challenge: how far can you improve this strategy?
One hint: it is possible to save all but one dwarf!

---

### Post by K.Mandla on 2008-11-26
Moved to Cafe Games.

---

### Post by billgoldberg on 2008-11-26
It's simple;

The dwarfs rush the witch and push her in the fire.

All the dwarfs are saved.

Counting tricks are inferiour, as none of them can provide a solution in which all the dwarfs are saved.

---

### Post by Idefix82 on 2008-11-26
> **billgoldberg said:**
> It's simple;

The dwarfs rush the witch and push her in the fire.

All the dwarfs are saved.

Counting tricks are inferiour, as none of them can provide a solution in which all the dwarfs are saved.

You have clearly never had to deal with vicious witches and I hope you never will. One move of the magic wand and all the dwarves are turned into stone or into Microsoft Word telephone support staff or something similarly terrible. No, no, the dwarves had better play by the witch's rules.
Edit: As you may have realised, I will not actually be able to reward the correct answer with a "Thanks" because the staff have moved this post into a category in which people are ungrateful by design. So I hope that the mental challenge will provide sufficient rewards for you.

---

### Post by kernelhaxor on 2008-11-26
Finally, got it.  so basically the first person (the one who can see all others) yells out 'red' if there are an even number of red hats in front of him and 'blue' otherwise.  So then the second person can count the number of red hats in front of him and depending on what the first person said, can guess his hat's color.  Third person too can do the same given that he has heard what the 2nd person said and see all the other hats in front of him and so on everyone can correctly guess the color of their hats.
Everyone except the first one will be saved for sure.

I feel stupid for taking three stabs to solve this problem!](*,)

> **Idefix82 said:**
>  As you may have realised, I will not actually be able to reward the correct answer with a "Thanks" because the staff have moved this post into a category in which people are ungrateful by design. So I hope that the mental challenge will provide sufficient rewards for you.

I wasn't doing it for the thanks anyway.  I love solving problems, challenging ones.

Thank you for the puzzle!

---

### Post by bapoumba on 2008-11-26
> **Idefix82 said:**
> 
Edit: As you may have realised, I will not actually be able to reward the correct answer with a "Thanks" because the staff have moved this post into a category in which people are ungrateful by design. So I hope that the mental challenge will provide sufficient rewards for you.
The Thank You feature has been designed for aknowledging a useful post, not as a reward ;)
If members have fun playing your game, they'll play, and the Cafe Game section is the one they'll go to play. Cheers!

---

### Post by Idefix82 on 2008-11-26
> **kernelhaxor said:**
> Finally, got it.  so basically the first person (the one who can see all others) yells out 'red' if there are an even number of red hats in front of him and 'blue' otherwise.  So then the second person can count the number of red hats in front of him and depending on what the first person said, can guess his hat's color.  Third person too can do the same given that he has heard what the 2nd person said and see all the other hats in front of him and so on everyone can correctly guess the color of their hats.
Everyone except the first one will be saved for sure.


Well done!
On to the next chapter of the story: The witch decides that next time she captures dwarves, she will have to make the rules harder to get more victims. So she catches 100 dwarves again and plays the same game with them but this time she uses 10 different colours. Of course the dwarves don't know how many hats of each colour there are in total (although they do know which colours are available). Same rules apply as in the first riddle. How many dwarves can be saved this time?

---

### Post by mali2297 on 2008-11-30
Since nobody else cared to answer, I will give my solution to the problem. It is written below in white text.

> [color=white]
Associate each colour with a number 0 to 9. 

The first dwarf sums up the numbers/colours of the hats in front of him and says the last digit of the sum (according to the decimal system). He will only have a 10 % chance of being saved.

The second dwarf knows the sum of the 98 hats in front of him and the last digit of the total sum including himself (but excluding the first person). From this information, he can infer the colour of his own hat. For instance, if the sum of all hats but his own is 567 and the last digit is 3, then his hat must have the colour 6. He says the correct answer and is saved.

Next, the third person knows the colour of the hat on the person behind him (from overhearing the correct answer), the colours of the hats on the persons in front of him and the last digit of the total sum (again excluding the first person). By the same principle, he too can correctly say the colour of his own hat. 

Repeat the procedure for dwarf number 4,5,...,100. 

In conclusion, all but the first dwarf can be saved with certainty.
[/color]

---

### Post by Idefix82 on 2008-11-30
Thank you for this wonderful solution,!
So in general, we get the result (which may seem rather surprising at first glance) that if you have n dwarves (say n=10000) and k colours, where k<n, then all but the first dwarf can be saved. The procedure is the same as that explained by mali2297 but instead of considering the last digit, one has to consider the remainder of division by k (note that the last decimal digit of a number is just the remainder of division by 10).

I will wait a little to see whether anybody has any questions about this riddle or whether anybody would like to offer a puzzle himself.

---

### Post by CJ Master on 2008-11-30
[This looks very familiar... :?](http://ubuntuforums.org/showthread.php?t=994463)

---

### Post by Idefix82 on 2008-12-02
OK, so here comes the next sequel of the witch-dwarf thriller:
The witch has found an other village with 100 dwarves and this time she is sure that the task she is going to set will be too tough for them:

In a minute the dwarves will be seated in a circle, each dwarf seeing all the other ones. They will each get a hat, which will have one of 100 predetermined colours (they don't know how many of each colour there are, so their hats could all be the same, or all different, or anything in between). Then they will be asked to quietly write down on a piece of paper their guess for their own colour, nobody seeing the guesses of their neighbours. The witch will go round and have a look at all the papers. If one dwarf guesses correctly, they are all released. If all of them guess incorrectly, they will all be forced to hunt Microsoft viruses for the rest of their lives.

They have 1 minute to think of a strategy. How can they maximise their probability of escaping?

---

### Post by mkrahmeh on 2009-04-18
it looks like a hard one. you need not to say that there are no assumptions like passing papers or so..right ? meaning that the solution is quite logical like the previous one ?

---

### Post by CJ Master on 2009-04-18
There's already a topic for this, check my link in the post above.

---

### Post by Idefix82 on 2009-04-20
> **mkrahmeh said:**
> it looks like a hard one. you need not to say that there are no assumptions like passing papers or so..right ? meaning that the solution is quite logical like the previous one ?

Yes, there is no cheating involved. A small hint: solve the same puzzle with 2 dwarves instead of a 100 first. So there are 2 dwarves and each will get a white or a black hat. They can see each other. The rest is the same as in the previous puzzle.

---

### Post by mkrahmeh on 2009-04-20
if the two dwarves agreed to use the same colour beforehand, one of them will get the correct answer, right ?
shall i proceed from this assumption on ?

is that popcorn ?
:popcorn:

---

### Post by Idefix82 on 2009-04-22
> **mkrahmeh said:**
> if the two dwarves agreed to use the same colour beforehand, one of them will get the correct answer, right ?
shall i proceed from this assumption on ?


No, there is no guarantee that their colours are different. They could both have white or both have black. Similarly, in the 100 dwarves scenario, all 100 could have the same colour. Or they could all have different colours. Or anything in between.

---

### Post by mkrahmeh on 2009-04-22
ok then, for the 2 dwarves problem, its easy: 
the first will answer the same colour of the second, but the second will answer the opposite of the first's colour

there are 4 possibilities, but i think order is not important here, so there are 3 actually:

(white, white), (white, black), (black, black). answers will be: 
(white, black), (black, black), (black, white)

in all cases, there is always a match..are there more hints ? supporting heuristics ?

---

### Post by Idefix82 on 2009-04-23
> **mkrahmeh said:**
> ok then, for the 2 dwarves problem, its easy: 
the first will answer the same colour of the second, but the second will answer the opposite of the first's colour

there are 4 possibilities, but i think order is not important here, so there are 3 actually:

(white, white), (white, black), (black, black). answers will be: 
(white, black), (black, black), (black, white)

in all cases, there is always a match..are there more hints ? supporting heuristics ?

Right, now try to understand as well as possible why this works (not by enumerating all the cases) and see if you can generalise it to the 100 dwarves case.

---

