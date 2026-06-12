---
title: "Number puzzle"
date: 2009-11-04
forum: Cafe Games
---

### Post by blazemore on 2009-11-04
Can you work this one out?
No prizes, just for fun.

What are the next 2 numbers in this sequence, and what is the definition for this sequence?

0, 1, 1, 3, 5, 11, 21, 43, 85, 171, 341

---

### Post by ZankerH on 2009-11-04
Is this a game where you answer the question, then post your own question?

Since you didn't define a sequence, here's an easy one to start the thread off:

e_0=Sqrt(2);
e_n=Sqrt(2+e_(n-1))

Where e_0 is the 0-th element and e_n is the generic element. What does the sequence converge to? Does its sum converge?

---

### Post by ZankerH on 2009-11-05
> **blazemore said:**
> 0, 1, 1, 3, 5, 11, 21, 43, 85, 171, 341

Definition: element(n) = (element (n) + 2* element (n-1)).

The next two elements are 683 and 1365.

I've already posted my sequence and questions.

(Please don't turn this into a "do my highschool math homework" thread)

---

### Post by s.fox on 2009-11-05
> **blazemore said:**
> can you work this one out?
No prizes, just for fun.

What are the next 2 numbers in this sequence, and what is the definition for this sequence?

0, 1, 1, 3, 5, 11, 21, 43, 85, 171, 341


0, 1, 1, 3, 5, 11, 21, 43, 85, 171, 341, [color=red]683, 1365[/color]

---

### Post by risby on 2009-11-05
> **ZankerH said:**
> Definition: element(n) = (element (n) + 2* element (n-1)).

The next two elements are 683 and 1365.

I've already posted my sequence and questions.

(Please don't turn this into a "do my highschool math homework" thread)
In maths you can't define element(n) as element(n) + something. Your equation is meaningless so you haven't shown how you generated the next two elements in the series. 683 is twice 341 plus 1 but 1365 is twice 683 minus 1 and, working back, this fits the series.

I guess the series equation is

X(n+1) = 2X(n) + (either -1 or 1 depending on whether n is odd or even)

Perhaps you could use n mod 2 to get 0 or 1, multiply by 2 to get 0 or 2 and then subtract 1 to get -1 or 1

So
[FONT=Courier New]   X(n+1) = 2 . X(n) + (2 . (n mod 2) - 1) where X(1) = 0
[/FONT]e.g.
[FONT=Courier New]   X(1)   = 0                                      [COLOR=Blue](as stated)[/COLOR]
   X(2)   = 2 .  0    +  (2 . (1 mod 2) - 1) =   1,[COLOR=Blue]  i.e.  1 + 2 . 0[/COLOR]
   X(3)   = 2 .  1    + (2 . (2 mod 2) - 1) =   1,[COLOR=Blue]  i.e. -1 + 2 . 1[/COLOR]
   X(4)      = 2 .  1    +  (2 . (3 mod 2) - 1) =   3,[COLOR=Blue]  i.e.  1 + 2 . 1[/COLOR]
   X(5)      = 2 .  3    +  (2 . (4 mod 2) - 1) =   5,[COLOR=Blue]  i.e. -1 + 2 . 3[/COLOR]
[/FONT][FONT=Courier New]   X(6)      = 2 .  5    +  (2 . (5 mod 2) - 1) =  11,[COLOR=Blue]  i.e.  1 + 2 . 5[/COLOR]
[/FONT][FONT=Courier New]   X(7)      = 2 . 11    +  (2 . (6 mod 2) - 1) =  21[/FONT][FONT=Courier New],[COLOR=Blue]  i.e. -1 + 2 . 11[/COLOR][/FONT]
[FONT=Courier New]   X(eight)      = 2 . 21    +  (2 . (7 mod 2) - 1) =  43[/FONT][FONT=Courier New],[COLOR=Blue]  i.e.  1 + 2 . 21[/COLOR][/FONT]
[FONT=Courier New]   X(9)      = 2 . 43    +  (2 . (8 mod 2) - 1) =  85[/FONT][FONT=Courier New],[COLOR=Blue]  i.e. -1 + 2 . 43[/COLOR][/FONT]
[FONT=Courier New]   X(10)     = 2 . 85    +  (2 . (9 mod 2) - 1) = 171[/FONT][FONT=Courier New],[COLOR=Blue]  i.e.  1 + 2 . 85[/COLOR][/FONT]
 [FONT=Courier New]   X(11)     = 2 .171    +  (2 .(10 mod 2) - 1) = 341[/FONT][FONT=Courier New],[COLOR=Blue]  i.e. -1 + 2 . 171[/COLOR][/FONT]
  [FONT=Courier New]   X(12)     = 2 .341    +  (2 .(11 mod 2) - 1) = 683[/FONT][FONT=Courier New],[COLOR=Blue]  i.e.  1 + 2 . 341[/COLOR][/FONT]
  [FONT=Courier New]   X(13)     = 2 .683    +  (2 .(12 mod 2) - 1) =1365[/FONT][FONT=Courier New],[COLOR=Blue]  i.e. -1 + 2 . 683[/COLOR][/FONT]

---

### Post by ZankerH on 2009-11-05
> **risby said:**
> In maths you can't define element(n) as element(n) + something. Your equation is meaningless so you haven't shown how you generated the next two elements in the series.

The error is pure syntax, since I've obviously calculated the next two elements, and defined the sequence in English. Now solve the one I've posted.

---

### Post by blazemore on 2009-11-06
Call the function J

```

J(n+1) = 2J(n)+(-1)^J(n)

```

---

