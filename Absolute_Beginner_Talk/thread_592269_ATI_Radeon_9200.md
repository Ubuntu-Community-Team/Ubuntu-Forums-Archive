---
title: "ATI Radeon 9200"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by m-k-m on 2007-10-26
So here is my problem:
I have ATI Radeon 9200 graphical Card and I installed Ubuntu 7.10 and I have one CRT monitor 19" (default screen) and one LCD 17". So the monitors are showing me the same picture (desktop) so I tried to solve this in System-> Administrations-> Screens And Graphics, but I can't make my 17" lcd  my secondary monitor (I've tried almost every driver in the "Graphic card" properties)

So can anybody help me with this?

thanx, 

matko

---

### Post by 11touche on 2007-10-27
Similar problem here, and the only thing that worked for me was to roll back to the old Xorg version from Feisty repositories, and take my old xorg.conf as it worked under Feisty.

---

### Post by outkast08 on 2007-11-03
It seems like my ATI card is slow on Ubuntu, I am currently using Ubuntu Gutsy. I tried running MotoGP 3 under wine and it is very slow... I can play that game just fine under Windows XP, I'm running on dual boot Ubuntu/WindowsXP. And I am gettin low fps on America's Army Client 2.5, even unplayable slow on SF Maps like Urban, I am disappointed   so I removed ArmyOps. I haven't tried installing a Windows version of ArmyOps under windows XP I can't tell if it has no problem there.

this is what shows up when I run lspci on the terminal... this is the video card part right?
**01:00.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)**

I attached a screenshot of my Screen and Graphics settings:
[ATTACH]49004[/ATTACH]

And a copy of my xorg.conf
**_[ATTACH]49007[/ATTACH]_**

this is what shows up in the terminal when I run glxgears...
[B]~$ glxgears 
6159 frames in 5.0 seconds = 1231.649 FPS
5974 frames in 5.0 seconds = 1194.761 FPS
6139 frames in 5.0 seconds = 1227.677 FPS
3485 frames in 5.0 seconds = 696.024 FPS
583 frames in 5.0 seconds = 116.405 FPS
1790 frames in 5.0 seconds = 357.991 FPS
4717 frames in 5.0 seconds = 942.007 FPS
580 frames in 5.0 seconds = 115.881 FPS
587 frames in 5.0 seconds = 117.338 FPS
766 frames in 5.0 seconds = 153.084 FPS
783 frames in 5.0 seconds = 156.416 FPS
614 frames in 5.0 seconds = 122.672 FPS
580 frames in 5.0 seconds = 115.998 FPS[/B]

Am I using the right setup for my ATI Radeon card on my Ubuntu?

---

### Post by doggiedoll on 2007-11-12
> **11touche said:**
> Similar problem here, and the only thing that worked for me was to roll back to the old Xorg version from Feisty repositories, and take my old xorg.conf as it worked under Feisty.

How could we roll back from Gutsy to use Feisty xorg? I really need to do the same thing?

---

