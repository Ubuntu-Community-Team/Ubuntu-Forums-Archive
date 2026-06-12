---
title: "Vanilla Kernel"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-11-26
I just updated to the Vanilla Kernel (is what it says under uname -r 2.6.14-chk1)
and anyways i had my wireless card detected b4 the reboot, and now the wireless card isn't being seen at all, and i STILL DON'T HAVE SOUND. 

can someone please help me! i don't have anything on my system at all should i just re-install 5.10? i wanna use linux but its seeming very tough, all i want on it is sound and internet and by trying to fix one problem my internet is now gone lol....and my java libs lol

WOULD BE MUCH APPRECIATED!!!!!

THX,cheers,
ad

ps. sorry for yelling lol

---

### Post by 23meg on 2005-11-27
You probably didn't compile with support for your wireless card. How exactly did you upgrade to 2.6.14?

---

### Post by adduds on 2005-11-27
lol i have no idea how i updated to 2.6.14 hahaha, i just followed these madd instructionss. I'm trying to get sound on my laptop to work, but i can't get it too...so i tried that vanilla kernel but after re-boot my wireless card (etho1) wasn't detected and my sound still didn't work. so i just re-installed, and i just installed java 1.5.0.

BUT MY SOUND STILL DOENS'T WORK

---

### Post by 23meg on 2005-11-27
Which "mad" instructions? That's what I'm asking; the reason your wireless isn't working may have to do with what exactly you compiled into your kernel. Chances are you forgot to compile support for your wireless card into it. And maybe you had to add support for your sound card as well. There's no way anyone can help you without knowing what your sound and wireless cards are and what how exactly you built the kernel.

---

### Post by adduds on 2005-11-27
These are the instructions i got: [http://ubuntuforums.org/showthread.php?t=84174](http://ubuntuforums.org/showthread.php?t=84174)

As for sound card: 

Intel 82801DB-ICH4

cheers,

ad

---

