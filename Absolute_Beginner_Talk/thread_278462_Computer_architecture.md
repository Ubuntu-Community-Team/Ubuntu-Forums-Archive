---
title: "Computer architecture"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by greisen on 2006-10-16
Hey all,

Just installed Ubuntu and it is great. I have a problem that I would really like to solve. If I determine my computer architecture with 

uname -m 

I get 

i686 

which I would expect. But when I try to run a program with the command sysname - I get the following strange error:

no computer architecture supported by TURBOMOLE "i786-pc-linux-gnuoldld"

TURBOMOLE is the program I am running. How to fix this problem?

Thanks in advance

---

### Post by Bachstelze on 2006-10-16
hmm, I don't know this soft but maybe

```
sudo apt-get install linux-686
```

could help

---

### Post by xyz on 2006-10-16
```
uname -r

or

uname -a
``` I think is what you want.

OOps! Sorry I misunderstood the question.

---

### Post by greisen on 2006-10-16
I dont see how that solves my problem? 
uname -r or uname -u 
It still gives me the right architecture for my machine. I still get the error that it is wrong architecture when I try to compile the program.

---

### Post by Lord Illidan on 2006-10-16
You are installing from the wrong package. They have these available :

i686-pc-linux-gnu, i786-pc-linux-gnu,
         	 				athlon-pc-linux-gnu, x86_64-pc-linux-gnu

You need to install the i686 one. That's what I gathered from their website, at least.

---

### Post by greisen on 2006-10-16
could you please expand a little bit on the wrong package - yes i want to install i686-linux-gnu. ¨

So where do I make the mistake? 

Thanks again

---

