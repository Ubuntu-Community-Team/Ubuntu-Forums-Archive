---
title: "Clock changes??"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by TheNemeses on 2007-01-23
Ok i have 2 different harddrives ubuntu is master, windows is slave and i ahve it on a mount chain using grub so i can switch between linux and windows at bootup. my problem is the time on the clock of both of the systems. when i change the time on one, it changes the time on the other one. 1. how does that work? 2. how do i fix it?

---

### Post by j19sch on 2007-01-23
I believe it has to do with how Windows and Linux interact with the hardware clock (you can access it directly through the BIOS settings> I'm having the same problem, but haven't tried to fix it yet.
I think I'll try setting an incorrect time zone in Windows, since most of the time I use Ubuntu.

---

### Post by TheNemeses on 2007-01-23
idk about that cause my bios doesnt change only the OS's... theres something not right, idk.

---

### Post by j19sch on 2007-01-23
Damn. There goes my easy fix! :)

---

### Post by edwardLS on 2007-01-23
I wish I could remember who to give credit for what fixed the problem for me, but I can't.  Needless to say, I received a fix on this forum.

I have a dual boot, WinXP and Ubuntu, with the local time set in the BIOS.  Windows displays the local time which is my desire.  Ubuntu 'was' displaying the incorrect time with an error factor of the delta between my local time and UTC time.  

My problem was fixed by editing the file /etc/default/rcS.  In that file is a value of UTC=yes; I changed that to UTC=no and my problem was fixed.

---

### Post by TheNemeses on 2007-01-23
i did that but it didnt change anything, is there something else im missing?


EDIT: haha nevermind had to change a setting, i got it to work now, ty sooooooooooo much.

---

