---
title: "Help, How to do recovery to old state"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by hisham777 on 2007-08-09
Hello there, im quite new to Ubuntu.

her is the problem 

When i start ubuntu it reach to 

* Checking root file system
fsck 1.++ 
/dev/sda1 containes a file system with error, check forced.
**** Some stuff
****
****
**** Some stuff End
fsck died with status 4

* an automatic file system check (fsck) of the root life system failed.


**** Some stuff
****
****
**** Some stuff End



Press Control D


if you want the details please let me know 

all i need is to know if Ubuntu can return the system to initial state like one day earlier with out the 
ROOT PASSWORD.

Please help me out.

---

### Post by be4truth on 2007-08-09
Read through this post and see if any of what this people did helps you. Otherwise come back.

[http://ubuntuforums.org/showthread.php?t=438361]("http://ubuntuforums.org/showthread.php?t=438361")

---

### Post by hisham777 on 2007-08-09
i did go to the recovery mode.

in the recovery mode it keep working untel it reach to the same state which is

* An automatic file system check (fsck) of the root file system failed.
A normal fsck must be performed, then the system restarted.
The fsck should be performed in maintenence mode with the
root file system mounted in read-only mode.
* The root file system is currently mounted in read-only mode.
A maintenence shell will now be started.
After performing system maintenence, press CONTROL-D
to terminate the maintenence shell and restart the system.
Give root password for maintenence
(or type CONTROL-D to continue):

**there is one thing though **

The problem is i dont have the root password 
i just need the system to back to its state one day ago.

anybody help please.

---

### Post by splintercellguy on 2007-08-09
Strange that it prompt for root password, you didn't toy with the account by chance did you? Assuming you get some sort of shell, just type fsck.

---

### Post by hisham777 on 2007-08-09
i connected my external harddrive to Ubuntu and for some resoune i disconnected it with out Unmonte,

and i restarted the system, then the problem came out.

please code some on tell me step by step on how
to run the fsck manualy

please help me out or ill get scrowed by my boss (if his mood is good ill get fired only)

Please.

---

### Post by splintercellguy on 2007-08-09
Try booting the LiveCD and doing fsck from there, or Recovery Mode?

---

### Post by Hospadar on 2007-08-09
By default there is no root password, have you tried just hitting enter?  If  you changed the root password at some point though and don't remember it, you may be out of luck.  You could also run fsck off the livecd.  If you can get at any files from the livecd, you may want to back up anything important (via the livecd) before fsck-ing your drive.

If you don't know how to run it, It runs from the terminal, and you'll want to run something like ```
fsck /dev/hda1
``` but the actual drive (hda1) will depend on how the livecd mounts your drives.  you can do a ```
df
``` to get drive info to figure out which drive to run it on.

You may need to do it with sudo, but with the livecd I don't think you will need that ```
sudo fsck /dev/whatever
```

You might also want to do a ```
man fsck
``` for more fsck options and info, or do some googling to figure out how best to use it.

---

### Post by hisham777 on 2007-08-09
> **Hospadar said:**
> By default there is no root password, have you tried just hitting enter?  If  you changed the root password at some point though and don't remember it, you may be out of luck.  You could also run fsck off the livecd.  If you can get at any files from the livecd, you may want to back up anything important (via the livecd) before fsck-ing your drive.

**please tell me more **

i actually dont have the root password because am not the admin. am using the system to do my work in the company, the boss make the access level so no body can play with system files.

however; all i need just to go back to the working state which is few hours ago 

please tell me more about the live CD.

by the way how to back up when i can access the system.


now am in this screen which state
ALERT! /dev/hdc1 does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian*****) Built in Shel (ash)

Enter help for a list of built in commands

/bin/sh: can't access tty; job control turned off

(initramfs)

---

### Post by be4truth on 2007-08-09
> **splintercellguy said:**
> Strange that it prompt for root password, you didn't toy with the account by chance did you? Assuming you get some sort of shell, just type fsck.

It always asks for the password. Under normal circumstances it is the user password! If the root password was never activated.

---

### Post by splintercellguy on 2007-08-09
No, it doesn't, at least the last time I did it. We're not talking about sudo here. But I guess it's worth a shot if desperate. And the LiveCD, ehhhhhhhhhhhhhhhhh. Billion ways to possibly resolve it.

---

### Post by hisham777 on 2007-08-09
I just found out i dont have the Live CD, AAAAAAAAAHhhhhhhhhhhhhhhhhhh

---

### Post by be4truth on 2007-08-09
Be careful now. You can loose all data on that box which might bring you more in trouble than just going to your boss and tell him (or is it a her!) what you did as presicely as you can. Your boss might have the skills to save what can  be saved while you risk with every step to screw the situation more and more up until it can't be repaired any more.
Do you like poker?

---

### Post by splintercellguy on 2007-08-09
Mm, Linux System Rescue CD? [http://sourceforge.net/project/showfiles.php?group_id=85811&package_id=88964](http://sourceforge.net/project/showfiles.php?group_id=85811&package_id=88964)

---

### Post by hisham777 on 2007-08-09
> **splintercellguy said:**
> Mm, Linux System Rescue CD? [http://sourceforge.net/project/showfiles.php?group_id=85811&package_id=88964](http://sourceforge.net/project/showfiles.php?group_id=85811&package_id=88964)

can it be run through the USB Flash Drive?

---

### Post by be4truth on 2007-08-09
> **splintercellguy said:**
> No, it doesn't, at least the last time I did it. We're not talking about sudo here. But I guess it's worth a shot if desperate. And the LiveCD, ehhhhhhhhhhhhhhhhh. Billion ways to possibly resolve it.

Be aware that hisham777 is a beginner. All this is good and fancy and I would love to have this box now here and figure it out but to do such a thing as beginner under stress is not fun.

---

### Post by splintercellguy on 2007-08-09
True, sorry. I know the LiveCD can be put on the USB stick, but I'm a bit pressed to find directions.

---

### Post by hisham777 on 2007-08-09
> **be4truth said:**
> Be aware that hisham777 is a beginner. All this is good and fancy and I would love to have this box now here and figure it out but to do such a thing as beginner under stress is not fun.

Bro trust me in the situation am in now ill try all the possibilities to make it work
Situation
-scared 
-angry
-tensed 
and shaking by the way :(


Can the live CD run through USB Flash Drive ?

---

### Post by splintercellguy on 2007-08-09
Yes, but I really don't know how. Absolutely sure you cannot go past the root maintenance password request?

---

### Post by hisham777 on 2007-08-09
> **splintercellguy said:**
> Yes, but I really don't know how. Absolutely sure you cannot go past the root maintenance password request?

So if the system ask for the root password maintenance, there is no way but the root password. ?

Please tell me not.

---

### Post by splintercellguy on 2007-08-09
Try entering your user password? Enter nothing? Just get to a prompt :(. And can you not just use Linux System Rescue CD?

---

### Post by hisham777 on 2007-08-09
> **splintercellguy said:**
> Try entering your user password? Enter nothing? Just get to a prompt :(. And can you not just use Linux System Rescue CD?

When i use Ubuntu there is no password or user name it start with out the user name and password.

Now when i start it stop at the Checking root system file 
then go to fsck for somewhere around 62% the prompt me to strat it manualy and ask for the password.

Control D to continue

:(

---

### Post by splintercellguy on 2007-08-09
I guess press Ctrl-D, then fsck?

---

### Post by hisham777 on 2007-08-09
i press Ctrl-D it restart the system.

---

### Post by hisham777 on 2007-08-09
Everybody,

i guess am doomed.

wish me lack with my boss.

thanks for trying, i guess linux is not for me. and bugy by the way ill just go back to Win

---

### Post by fumduck on 2007-08-09
sounds like fstab is screwed up??  ctrl d does not boot up system??

---

### Post by be4truth on 2007-08-09
> **hisham777 said:**
> Everybody,

i guess am doomed.

wish me lack with my boss.

thanks for trying, i guess linux is not for me. and bugy by the way ill just go back to Win

How often did you reinstall windows because you screwed something up. The best you can do is to install Ubuntu at home on a machine without any valuable data and play around.
Play around, make a mess, repair it if you can, reinstall if you can't until you are familiar with the Linux platform.
Don't give a baking cakes because the first one wasn't that great. Linux cakes are really tasty.
Linux is not buggy. Linux is Open Source software which is constantly under development. Hope you find a positive approach to Linux after this story.
I have a friend who stayed alone the rest of his life because the first relationship didn't work out. Can you imagine ....

---

### Post by raevin on 2007-08-21
> **hisham777 said:**
> So if the system ask for the root password maintenance, there is no way but the root password. ?

Please tell me not.

Why not just runlevel 1 and chpasswd for the root? (or chpwd, or something like that...forgot the command to change the password.)

---

