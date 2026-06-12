---
title: "Unable to install Ubuntu 7.04"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by yangli on 2007-08-27
[SIZE="3"][FONT="Verdana"]Hi, I am new for Linux and am trying to install Ubuntu 7.04 on my machine. 

The problem is I can't even install it. Everytime I tried to boot from CD and install it, the first screen I got is an error message "[COLOR="Red"]**Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?**[/COLOR]" Then I hit "Yes", and got some other screens of messages and I panicked. 

Could anyone please help me, Thank you very much![/FONT][/SIZE]

---

### Post by splintercellguy on 2007-08-27
Have you tried booting in safe graphics mode?

---

### Post by bodhi.zazen on 2007-08-28
What video card do you have ?

---

### Post by Marat Galiev on 2007-08-28
OK.You must boot in safe graphical mode,and if you X server start fails,press ctrl+alt+F2,
login,and do sudo nano /etc/X11/xorg.conf,find string with line ```
driver "nvidia"
```(or driver "ati"),i don't know you video card:)
And edit line like this 
```

driver "vesa".

```
Save changes and do
sudo /etc/init.d/gdm restart.
And use ubuntu with X:)

---

### Post by Jimmyfj on 2007-08-28
Alternately you could try downloading the alternate install Cd and see if this lets you install Ubuntu. Some specs on your system would make it easier for us to help you too.

---

### Post by yangli on 2007-08-28
Yes, I tried it again and used the safe graphical mode. It worked. Basically I just press "Next" all the way through without any problems. Thank you guys for the help. 

BTW: My video card is an onboard one, so I am not sure about what it is. 
Also, I stupidly installed Ubuntu in the same disk as Windows XP.:(:( So I think I have to start again tomorrow. But I now know how to do that. Thanks again. :):popcorn:

---

### Post by dwhitney67 on 2007-08-28
> **Jimmyfj said:**
> Alternately you could try downloading the alternate install Cd and see if this lets you install Ubuntu. Some specs on your system would make it easier for us to help you too.

It's funny that Ubuntu has two flavours of installation disks... one that sometimes works and another that always works (the alternate CD).  Yet people tend to go with the former.  :confused:

---

