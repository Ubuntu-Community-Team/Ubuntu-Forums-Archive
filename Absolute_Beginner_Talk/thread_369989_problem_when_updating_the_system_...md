---
title: "problem when updating the system .."
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by almasry on 2007-02-25
I face a problem when i try to write this command in the terminal  :  
> sudo aptitude update


and this is the error :

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
almasry@almasry:~$ 


what would be the problem ?? the problem appeared after  upgrading the system and editing the source list  ..
how can i solve this ??
thanks in advance

---

### Post by ve9cbc on 2007-02-25
Hello Almasry! 

Check to see if under Applications - System Tools if Root Terminal is there. That is the terminal you would have to use to enable what you want to accomplish. Also when you select it it will ask you for your password.

If the Root Terminal is not there, here is how to make it appear:

Select System - Menu Layout - System Tools then check Root Terminal. This will make the Root Terminal appear in your menu.

I hope this assist you.:)

---

### Post by almasry on 2007-02-25
no , it is not a terminal proplem ...
because the same error appears when i tried to run (Add/remove) from the application menu ..

the system was working for 2 days  updating from here and there .. and needed a restart , wich was notified after this post ..

i made a restart and every thing went ok ..

thanks for ur help :)

---

### Post by Mornedhel on 2007-02-25
You need to be root (sudo or su) and not to have any apt-something running at the same time. For instance, you cannot apt-get install some_package if you are running Synaptic at the same time.

---

