---
title: "I cant boot into refit or dd"
date: 2014-07-21
forum: Apple Hardware Users
---

### Post by jackson10 on 2014-07-21
Okay so I am trying to dd like so dd: /dev/rdisk1s1: Input/output error201+0 records in
200+0 records out
209715200 bytes transferred in 45.632187 secs (4595774 bytes/sec)
Jacksons-MacBook-Pro:~ jacksonfain$ 
that happens and im just confused the only issue I HAVE NO IDEA HOW TO BOOT INTO REFIT like at I looked it up all over the place someone please help me

---

### Post by este.el.paz on 2014-07-22
> **jackson10 said:**
> Okay so I am trying to dd like so dd: /dev/rdisk1s1: Input/output error201+0 records in
200+0 records out
209715200 bytes transferred in 45.632187 secs (4595774 bytes/sec)
Jacksons-MacBook-Pro:~ jacksonfain$ 
that happens and im just confused the only issue I HAVE NO IDEA HOW TO BOOT INTO REFIT like at I looked it up all over the place someone please help me

@jackson:

I can't help you with dd . . . but I don't think dd has anything to do with rEFIt . . . ??  dd is to copy stuff from one disk to another??  rEFIt is a system boot selector . . . it helps the system to "recognize" the various boot options you have, i.e., you have OSX 10.6.8 in one disk, and you have linux in another.  But rEFIt only works up to either 10.6 or 10.7 . . . the new update for systems after that is rEFInd . . . .  You can find it on "sourceforge" or googling it and looking for "rodbooks" . . . he has a web site that shows you how to install it . . . it can be quite complicated, or easy . . . I picked the "easy install on OSX" . . . .

I prefer to set up the dual boot or triple boot disks (whatever you choose) using Disk Utility rather than Bootcamp . . . BC seems to "lock you in" to whatever choice you make at the time, I couldn't modify the HD after I used BC the first time I did this . . . using rEFIt.  The second time I did it using DU and installing rEFInd . . . .

So, first thing, rEFIt or rEFInd has to be installed . . . then you should just be able to restart the computer and the rEFIt window ***should*** load; mine did the first couple times, then it stopped, so now I hold the "option" key down while re-booting . . . but, I have my rEFInd installed in front of the second disk, rather than in front of the first as many folks do it . . . .  I wanted the "default" system to be OSX 10.6.8, so if I just reboot it naturally goes to 10.6 . . . if I hold the option key I get the OSX boot manager, which shows a "windows" disk, but it's linux, or, if I click on disk two it opens to the rEFInd manager . . . and I can pick any of the options through it . . . . 

Good luck,

e.e.p.

---

