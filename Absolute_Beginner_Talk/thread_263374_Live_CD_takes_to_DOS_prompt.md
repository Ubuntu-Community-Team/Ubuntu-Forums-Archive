---
title: "Live CD takes to DOS prompt"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by jayramj on 2006-09-23
A total ubuntu newbie here.

I have kububtu(tried with ubuntu CD as well) 6.06.1 Live CD. When I try to boot from this CD, I see some messages and then shown a dos prompt. Never get to see boot screen or any graphical display at all

Happens on a Dell Lattitude 610 as well as my custom built desktop

Any pointers?

Thanks
Jayram

---

### Post by YeahBuntu on 2006-09-23
So you never get to see any screen that says something like check this CD?

I would maybe try to download again burn again at a slower rate? maybe 12x?

I never had any problems with the Live CD myself but I see plenty of others having issues with the live cd.  How much ram do you have on your 'pcs' ?

---

### Post by slimdog360 on 2006-09-23
Its called a terminal or console not dos prompt. As for the question, did you download the server install cd. If so you should have downloaded the desktop cd.

If you did download the dektop install can you list your computer specs.

---

### Post by jayramj on 2006-09-23
Nope I dont get any such message. I see a message which says something about Debian, then a bunch of messages(most likely related to hardware detection) which scroll up very fast. Then I end up with a DOS Prompt

I have 1GB+ Ram. Laptop is intel based and desktop is AMD.

I will try to burn the CD at a slower speed and see what happens

Thanks
Jayram

> **YeahBuntu said:**
> So you never get to see any screen that says something like check this CD?

I would maybe try to download again burn again at a slower rate? maybe 12x?

I never had any problems with the Live CD myself but I see plenty of others having issues with the live cd.  How much ram do you have on your 'pcs' ?

---

### Post by jayramj on 2006-09-23
The image reads "kubuntu-6.06.1-desktop-i386.iso" so its a desktop install

What I see is really a "DOS" shell.

Specs:
Intel Pentium M processor(1.73 GHz)
2 GB RAM
Windows XP SP1


> **slimdog360 said:**
> Its called a terminal or console not dos prompt. As for the question, did you download the server install cd. If so you should have downloaded the desktop cd.

If you did download the dektop install can you list your computer specs.

---

### Post by MWAAAHAAA on 2006-09-23
> Nope I dont get any such message. I see a message which says something about Debian, then a bunch of messages(most likely related to hardware detection) which scroll up very fast. Then I end up with a DOS Prompt

Seems like a shell to me. Can you post *exactly* what you end up with?

---

### Post by jayramj on 2006-09-23
A Prompt like this

[DR-DOS] A:\>

Directory listing shows

DRDOS   <DIR>
OAK     <DIR>
NR      <DIR>
WWBMU EXE

If I run WWBMU it takes me to some german page. When I go on pressing enter, I endup on a screen which probably wants me to specify partitions etc. 

Since its all german cant make any sense out of it


> **MWAAAHAAA said:**
> Seems like a shell to me. Can you post *exactly* what you end up with?

---

### Post by arkangel on 2006-09-23
at least we know your problem , you have a WWBMU Boot Manager  , a stupid german boot manager, fist try to get rid of that 

cannot you boot direclty from the cd? (by pressing esc or f2 just before all start or entering in the bios and forcing the cd to be 1. drive to load )

the laptop  should run a live cd  for 32 bits (the most used ) ,for your desktop try with the AMD 64 bit iso

Edit: can you post a picture  or the options you have  , if it is not too big i 'll try to translate , maybe there is and option "deinstallieren"

---

### Post by jayramj on 2006-09-23
Arkangel,

I am booting directly from LiveCD. As I said in earlier messages it says its loading Linux.. then shows a bunch of messages then throws me to the prompt. Just for sake of it I did a dir there and found WWBMU. So I am not using anything outside whatever I got from LiveCD

> **arkangel said:**
> at least we know your problem , you have a WWBMU Boot Manager  , a stupid german boot manager, fist try to get rid of that 

cannot you boot direclty from the cd? (by pressing esc or f2 just before all start or entering in the bios and forcing the cd to be 1. drive to load )

the laptop  should run a live cd  for 32 bits (the most used ) ,for your desktop try with the AMD 64 bit iso

Edit: can you post a picture  or the options you have  , if it is not too big i 'll try to translate , maybe there is and option "deinstallieren"

---

### Post by arkangel on 2006-09-23
Hi i read some german  posts , try the following 

boot into windows ,and uninstall it  , most probably in add/remove sotfware
....
then try again

---

### Post by jayramj on 2006-09-23
Solved the problem. It seems the ISO image wasnt written properly. Stupid CD Writters from WinXP and Nero. Used the CD burning software given in this post..

[http://www.ubuntuforums.org/archive/index.php/t-15294.html](http://www.ubuntuforums.org/archive/index.php/t-15294.html)

And it worked !! I can see ubuntu loaded and the desktop now. Sweet!!

Thannks to all those who replied

Jayram

> **arkangel said:**
> Hi i read some german  posts , try the following 
boot into windows ,and uninstall it  , most probably in add/remove sotfware
....
then try again

---

