---
title: "PLEASE HELP!! (with installation)"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2008-03-04
I cannot get Ubuntu to load onto a brand new Compaq Athlon 64 laptop. It continually fades to white. I've attempted to load 7 different linux varieties, used text-only instalation and everything I can think of. The disk always check out (md5 are legit and no errors) Sometimes the OS gets installed and then on first boot it loads about half way and then fades, other times it doesn't even get that far. Please, please give me step by step instruction. I've loaded Ubuntu onto my desktop with no problem. This is my little sister's _Christmas_ present and I still have it. I was trying to do her a favor and protect her from viruses. Please, please help:(:(:(:(:(

---

### Post by glennric on 2008-03-04
When does it fade to white?  What happens before it gets to that point?  Is it when you are loading the live cd, or installing, or after the install?  More information is needed to diagnose the problem.

---

### Post by woodsonoversoul on 2008-03-04
As I've said, at all points. Lately I've been trying with Ubuntu 7.10 alternative CD. It installs the OS pauses at the final reboot (after I eject the CD) and then will partially load (I get about 2/5 of the load progress bar) and then it fades

---

### Post by glennric on 2008-03-04
Have you been able to successfully boot the live cd?  Do you know any specific details about the hardware of the maching?  In particular what video card it has?

---

### Post by woodsonoversoul on 2008-03-04
bump
 I'm trying to reboot it. Now instead of fading to white, it's freezing (at the same point)

---

### Post by woodsonoversoul on 2008-03-04
Nivida makes the video card. That's really all I know. I'll try re-downloading a live cd, but it hasn't worked before. I've been working on this a couple of hours a week for over three months

---

### Post by glennric on 2008-03-04
Could you try booting to the installation and when the grub menu comes up (you may have to hit ESC to bring up the menu) hit "e" to edit the boot selection.  Change the word "splash" to "nosplash" and add the word "verbose" and hit enter.  Then hit "b" to boot.  This should take the splash screen off and show more information.  Then try to see exactly where it starts having trouble.

---

### Post by woodsonoversoul on 2008-03-05
should i change the word quiet to verbose?

---

### Post by woodsonoversoul on 2008-03-05
Alright. Changed "splash" to "nosplash", left "quiet", and added the line "verbose". When I hit "b" to boot it progresses to the progress bar, fills that (which is more than it did before) and then fades to white. Not a lot more info :(

---

### Post by woodsonoversoul on 2008-03-05
bump

---

### Post by jseiser on 2008-03-05
I would say at this point, we need to know the hardware of the PC.  even if you have to open it up and get that info.  It has to be some odd hardware configuration, or a faulty part.  Just as a question, did this PC work when it had windows? or was it purcahsed barebones?

---

### Post by DarinB on 2008-03-05
I know this may be a silly question but are you using a 64 bit version of ubuntu?
Can you install a windows on it?
or does it do the same thing?

---

### Post by woodsonoversoul on 2008-03-05
It worked when it had Vista. I'm going to look up the hardware online now

---

### Post by woodsonoversoul on 2008-03-05
via HP's website
AMD Athlon 64 X2 Dual-Core Mobile Technology TK-55; 1.8GHz
1024MB DDR2 SDRAM
Nvidia GeForce Go 6100 (UMA) with up to 288MB total available graphics memory
Up to 1600MHz system bus running at AC/DC Mode 35 watt

Anything else you need to know?

---

### Post by woodsonoversoul on 2008-03-05
I'm stepping out for just a minute. I'll reply to all post when I return. Thanks guys

---

### Post by woodsonoversoul on 2008-03-05
It is the 64 version. I don't have a spare copy of windows to try with

---

### Post by woodsonoversoul on 2008-03-05
bump

---

### Post by woodsonoversoul on 2008-03-07
and bump again. Has anyone encountered anything like this?

---

