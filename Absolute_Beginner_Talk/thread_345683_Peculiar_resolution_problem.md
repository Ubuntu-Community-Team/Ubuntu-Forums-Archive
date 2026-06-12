---
title: "Peculiar resolution problem"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by MickS on 2007-01-24
Please be gentle with me I am new to this, I installed Dapper a couple of weeks ago and had resolution problems like others so following advice elsewhere in the forum I now have the resolution sorted but I have a strange result when I start up the Ubuntu screen comes up fine until it gets to the log in screen which looks fine but I have a floating caption saying input not supported, I enter my login details and log in then everything is fine again :confused: 
A related problem is that when I go to the Add/Remove programs thing and click on it, all I get is the resolution setting panel popping up, I have no idea what to do about it please help.


Mick

---

### Post by phr0ze on 2007-01-24
I think one of your resolution settings is wrong during boot. I am new to linux so I can't tell you how to fix it but I can help you search. Try 'boot resolution not detected' or 'login resolution not detected'. 

My LCD gives the same floating window when my resolution is wrong.

---

### Post by jbayone on 2007-01-24
You can also change the resolution by sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by MickS on 2007-01-24
Thanks for that, I never thought of searching on Login resolution Doh, found loads of stuff to try tomorrow when I am not so tired.

Mick

---

### Post by MickS on 2007-01-27
Finally sorted it by setting the size to 17 inches instead of the 19 inches that it should be, in case that is of use anyone else. I ran  sudo dpkg-reconfigure -phigh xserver-xorg and accepted all the defaults.

Mick

---

