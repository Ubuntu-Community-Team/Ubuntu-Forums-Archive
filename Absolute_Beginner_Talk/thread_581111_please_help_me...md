---
title: "please help me.."
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-10-19
I installed latest ubuntu version (7.10)

when i am going to connect Remote Login via XDMCP , I click that corresponding IP address to connect 

then my system is going to connect ,and show some messages within a second (so i can't see the Error messages) and came to my own login page

how to solve this ?
and also how to see the error messages ?...

but i can connect that remote system using through SSH.


please help...
thank you....

---

### Post by Hospadar on 2007-10-19
did you set up remote connection on the host system?  Your old settings might have gotten wiped by the update.

---

### Post by mokkai on 2007-10-19
sorry for my late reply...
the host system is ubuntu 7.04...
i connected to host system when my version in ubuntu 7.04.
after upgrade to 7.10 in my system, the error occured 
i can see the host ip in XDMCP view list .

thx

---

### Post by nickmcg on 2007-10-19
> **Hospadar said:**
> did you set up remote connection on the host system?  Your old settings might have gotten wiped by the update.

I have the same problem.
Setting up 2 machines from scratch, one with feisty, the other with Gutsy, XDMCP enabled on both.

The feisty machine can remotely connect to Feisty and Gutsy   machines, but Gutsy machines cannot connect remotely to anything. It appears to be a client-side login problem.

Nick

---

### Post by mokkai on 2007-10-20
thank you for reply 

is there any way to solve this ? 
otherwise i should go to degrade (7.04)....

---

### Post by nickmcg on 2007-10-20
It looks like this has been reported as a bug [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/150193)

Nick

---

### Post by surajvijayan on 2007-10-25
Please check here: [http://ubuntuforums.org/showthread.php?t=565383&page=2](http://ubuntuforums.org/showthread.php?t=565383&page=2)

> **mokkai said:**
> thank you for reply 

is there any way to solve this ? 
otherwise i should go to degrade (7.04)....

---

### Post by lledurt on 2007-11-05
Why is this bug of low importance?  It seams like a show stopper to quite a few people.
 
P.J.

---

### Post by PryGuy on 2007-12-05
When will they fix the bloody bug?! It's really annoying and I DO NOT install Gutsy on my customers PCs because of that! I hate to say that but do they really test the software before they release it?

---

