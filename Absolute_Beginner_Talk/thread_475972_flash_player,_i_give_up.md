---
title: "flash player, i give up"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by gprok on 2007-06-16
I have try possibly everything so far and i cant have it to work.....maybe its because i have a AMD64 3000+....dunno really..... when you think about the fact that most of the pages on the internet are using this player, its hard to conceive how i could navigate the net without it or at least an equivalent...i dont mind using something else to read these pages....can someone help me im about to throw myself of the balcony ;)

Gprok

---

### Post by HotShotDJ on 2007-06-16
Did you follow the instructions given in your other thread on this same topic?  Are you running 32 bit version of Ubuntu or 64 bit version.  I have the latest version of flash running on my system using flashplugin-nonfree from the standard multiverse repository.

---

### Post by gprok on 2007-06-16
i have followed everything that was posted about my problem so far.......im not 100% sure but i think im using the 64 bit version  i have AMD64 3000+..........................thanks a lot !!!

Gprok

here'S: gprok@gprok-desktop:~$ sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for flashplugin-nonfree
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
gprok@gprok-desktop:~$

---

### Post by ugm6hr on 2007-06-16
There is no 64-bit Flash version (even in Windows).

Either try re-installing a 32-bit Ubuntu - i386 version (which I would recommend) - or search for flash 64 in these forums for a fix.

---

### Post by gprok on 2007-06-16
okie i think this might really be my bog.....hummm...anyway i was gonna install ubuntu studio which i beleive is 32 bit only....anyway my amd64 is 32 bit if im right

thanks so much

Gprok

---

### Post by gprok on 2007-06-16
is there a way in my actual ubuntu to know if its a 32 or 64 bit version ????????

---

### Post by Kobalt on 2007-06-16
There is a very easy solution to get flash working on Ubuntu64. See [this]("http://ubuntuforums.org/showthread.php?t=425672").

---

### Post by kane77 on 2007-06-16
> **gprok said:**
> is there a way in my actual ubuntu to know if its a 32 or 64 bit version ????????

try ```
uname -a
``` 
that should give you something like:
```
Linux kane-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux
``` mine is 64 bit (you can tell by the x86_64)

---

### Post by gprok on 2007-06-16
BIG BIG thanks to everyone especially Cobalt who got me in the right direction......yes flash player works great ijn a AMD64..............so glad now....

Gprok

---

