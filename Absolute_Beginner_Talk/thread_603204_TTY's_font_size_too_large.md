---
title: "TTY's font size too large"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by ProfessionalNewbie on 2007-11-04
Hi all,

When I press CTRL, ALT & F1 or F2 etc, the Font size seems about 12 or 14 points & I'd like to know how to change this (preferrably to about 8).

How do I go about doing this?

Thanks in advance.

PN.

---

### Post by Griffiss on 2007-11-07
Not entirely sure which fonts you want to change. You can change system-wide fonts in system => preferences => appearance, then the fonts tab.

You can change the fonts for just the terminal by opening terminal, then edit => profiles..., press the edit button, then font settings are on the general tab.

---

### Post by rubicon on 2007-11-07
Hey there, I think it's not about font sizes, but about screen resolution. When you press Alt+Ctrl+F2, you are sent in a "real" terminal. No graphics, no eye-candy :) 

All you can do is to set your screen resolution to 1024x768 or more... But I personally don't know how to do it...

And I also do want to know the answer.

---

### Post by rubicon on 2007-11-07
Okay now. Consider reading this: [https://lists.ubuntu.com/archives/ubuntu-users/2007-June/117543.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-June/117543.html)

However, there're some problems people are reporting...
For example, [http://ubuntuforums.org/showthread.php?t=260488](http://ubuntuforums.org/showthread.php?t=260488)
and a bunch of bugs at Launchpad.

I'll try to make my virtual terminals to look better.

I wonder if that'll work for you, ProfessionalNewbie

---

### Post by rubicon on 2007-11-07
Well, geez, I'm back from hell XD

Following instructions in [http://ubuntuforums.org/archive/index.php/t-454392.html](http://ubuntuforums.org/archive/index.php/t-454392.html) I got 1280x1024 in my virtual terminals. However, usplash at bootup and shutdown isn't justified properly. After all, i'm not using VT much, so i decided to reverse all what I've done. Fortunately successfully.

So there're two questions. 
1-What's "initramfs" thingy and 
2-what does "update-initramfs -u -k `uname -r`" command do?

I'm still newbie, so I need help to understand what I've just done with my system...

---

### Post by ProfessionalNewbie on 2007-11-14
Thanks Rubicon, I'll give that a try.
Btw, wikipedia has some info on [initramfs]("http://en.wikipedia.org/wiki/Initrd"), which is new to Ubuntu I've noticed than from previous versions - apparently it replaces the old initrd ... gee, so much to read up on when it comes to linux & changes so fast.

pn.

---

### Post by rubicon on 2007-11-14
Hmm, useful link, thanks!

I guess there are still some problems with initramfs because it is relatively new to kernel (2.6.x).

But if it gives more speed or flexibility, then it will be improving :)

^ Just my thoughts aloud :D

And - hey, please post your results here, ProfessionalNewbie, I'm curious what will happen :)

---

