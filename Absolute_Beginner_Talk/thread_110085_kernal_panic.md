---
title: "kernal panic"
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by Brigrat on 2005-12-30
I have performed the ultimate noob error, I think.
I tried to upgrade my kernal to the 686 smp, selected the k-7 in some stupid error and no can not boot unless I hit escape and select the last working kernal.  My questions are 
A:  Do i need to remove the incorrect kernal?  the instruction I was given do not seem to work correctly. "apt-get remove kernal- 2.6.12-10-k7.  it returns a package not found line.

B: can I do the correct kernal "apt-get install linux 686-smp and have that "over write?" the last kernal install?  

Any help would BE MOST GREATLY APPRECIATED!!!!

---

### Post by thekiller on 2005-12-30
you can use [COLOR="Red"]synaptic[/COLOR] to remove it too and then reinstall the kernel image of the kernel you wanna use.

---

### Post by Brigrat on 2005-12-30
Under what heading in synaptic would I look for that "pckage/kernal"

---

### Post by Brigrat on 2005-12-30
Hey thanks, for the kick start, got the 686-smp loaded, halted the grub as the k7 was still at the top of the list and then used the synaptic as you said.  running like a champ with "BOTH" processors just a hummin!  thanks again!:p

---

### Post by thekiller on 2005-12-30
After you open [COLOR="Red"]synaptic[/COLOR], click on search. Then a pop-up window will appear, just type [COLOR="Red"]kernel[/COLOR] and press OK.

It will show all possible searches with [COLOR="Red"]kernel[/COLOR] and lookout for the one which u think u installed incorrectly. Simply rightclick on top of it and select [COLOR="Red"]Mark for Removal [/COLOR]and then click on **[COLOR="Lime"]Apply[/COLOR]**

---

### Post by drfalkor on 2005-12-30
or, just type:
'sudo apt-get install linux-k7', and then everything you needs get installed :D

---

### Post by Brigrat on 2005-12-30
Thanks everyone, I did not make it clear in my first post.  I have dual PII processors and the stupidly installed k7 (for the AMD proc) was installed and killed my box.  I learned very fast that hitting escape lets you go back and choose a different kernal.  That allowd me to go in and effect the needed changes.  again thanks all!

---

### Post by thekiller on 2005-12-30
you are welcome. By the way, how is the cold up in Chicago ? Down here in galveston, its been weird...a couple of days ago had to turn on the heater, right now my a/c is on its full blast. :D

---

### Post by Brigrat on 2005-12-30
hey don't rub it in, although for a Chicago winter it has been better than average.  warm!!!!:p

---

### Post by thekiller on 2005-12-30
Apologies !:D

---

### Post by Brigrat on 2005-12-30
No worries!  going to put my self to bed here before the sun comes up thanks for all of the help.

---

