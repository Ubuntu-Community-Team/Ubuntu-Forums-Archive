---
title: "X server fails to start with ATI Radeon 9250"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Adamski on 2007-08-01
I just installed Linux for the first time, Ubuntu 7.04, and have it dual booting with Windows XP. The problem, is my ATI Radeon 9250 doesn't seem to work. When I tried to load several versions of Ubuntu, I got the same error message that X server failed to start. I switched to my integrated graphics card, and it works fine and dandy. Now when I wish to go to the other OS, I have to reboot, go into BIOS and change some settings, restart it, and move the cables over.

Here are pictures of the error. (Image tags weren't working)
[http://img518.imageshack.us/my.php?image=picture2001by0.jpg](http://img518.imageshack.us/my.php?image=picture2001by0.jpg)
[http://img238.imageshack.us/my.php?image=picture2004af8.jpg](http://img238.imageshack.us/my.php?image=picture2004af8.jpg)

---

### Post by skymera on 2007-08-01
it hasnt detected you screen =S
reconfigure xorg and should be fine :)

---

### Post by Rocket2DMn on 2007-08-01
> **skymera said:**
> it hasnt detected you screen =S
reconfigure xorg and should be fine :)

It probably set your integrated card as the default.
```
sudo dpkg-reconfigure xserver-xorg
```
When you get to the correct screens, select your video driver and your monitor's max resolution and everything less (TAB to move, SPACEBAR to select/enable).
Then start gdm
```
/etc/init.d/gdm start
```

---

### Post by Martin on 2007-08-01
Hi,

IGNORE IGNORE IGNORE. Just as I hit the return key I remembered my old friend 'Service; I'd obviously disabled gdm somewhere along the line. 

I've got a similar problem. I wasplaying around with hibernation and suspend setting on my laptop. Got it all more or less working but now when I reboot gdm doesn't start automatically. I can run startx or gdm and the gnomeworks fine - How do I get gdm to start right away?

---

