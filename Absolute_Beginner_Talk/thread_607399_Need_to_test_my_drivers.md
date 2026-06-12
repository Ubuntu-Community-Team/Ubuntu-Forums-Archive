---
title: "Need to test my drivers"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by watson!!!! on 2007-11-08
I'm trying to run the second life alpha grid, but every time I start it up, the screen goes blank, my mouse and keyboard freeze up, and I'm forced to alt-sysrq-o my way out of it. The readme says that it may because my drivers aren't updated. How do I check to see if that's the case? 

lspic output is:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)


My current driver is i810 Intel Integrated Graphics Chipsets, includins i810, i815, 830M, 845G, 852GM, 855GM, 865G, 915G, 915GM, and 945GM.

Also, the readme says that typing "sudo aticonfig --locked-userpages=off" in a terminal may help, but when I do enter it, it says "sudo: aticonfig: command not found." What's going on?

Step by step, please, I am bad with the terminal.

---

### Post by overdrank on 2007-11-08
> **watson!!!! said:**
> I'm trying to run the second life alpha grid, but every time I start it up, the screen goes blank, my mouse and keyboard freeze up, and I'm forced to alt-sysrq-o my way out of it. The readme says that it may because my drivers aren't updated. How do I check to see if that's the case? 

lspic output is:

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)


My current driver is i810 Intel Integrated Graphics Chipsets, includins i810, i815, 830M, 845G, 852GM, 855GM, 865G, 915G, 915GM, and 945GM.

Also, the readme says that typing "sudo aticonfig --locked-userpages=off" in a terminal may help, but when I do enter it, it says "sudo: aticonfig: command not found." What's going on?

Step by step, please, I am bad with the terminal.

HI you can use this command ```
glxinfo | grep direct
``` if the answer is yes then you are good. Then aticonfig command I believe will only work with ATI graphics card.

---

