---
title: "CPU History"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Rhumbline on 2007-07-07
I'm just taking a look at my System Monitor Resources and my CPU History shows the blue line constantly at 100%. The only processes running are firefox.bin 7% and system monitor 30% so who's using the rest?
I have a Celeron processor at 733MHz in an old computer I'm using to try Ubuntu.

Also, when I drag a window across the desktop it leaves a 'trail'. Is this because I have a poor graphics card? My screen refresh is 75Hz.

---

### Post by aidanr on 2007-07-07
some process running as root will be using the rest, view -> show all (or something like that) or run "top" in a terminal

> Also, when I drag a window across the desktop it leaves a 'trail'. Is this because I have a poor graphics card? My screen refresh is 75Hz.

could be that you don't have drivers installed for your card, what graphics card do you have?

---

### Post by Rhumbline on 2007-07-07
I don't know what my card is. Can I find out or do I open the box & take a look?

---

### Post by aidanr on 2007-07-07
```
lspci|grep VGA
```
```
glxinfo|grep renderer
```
```
glxinfo|grep direct
```

---

### Post by Rhumbline on 2007-07-07
I just had a look...no graphics card. The monitor socket goes straight to the motherboard.

---

### Post by aidanr on 2007-07-07
Ok so you have onboard graphics, I'd imagine the "trail" is because the cpu is running at full, did you find out what process was taking up the rest of the cpu?

---

### Post by Rhumbline on 2007-07-07
paul@paul-desktop:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
paul@paul-desktop:~$ glxinfo | grep renderer
OpenGL renderer string: Mesa GLX Indirect
paul@paul-desktop:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
paul@paul-desktop:~$

---

### Post by Rhumbline on 2007-07-07
This is what's using the CPU resources:

 4612 root      25   0  8580 5584 4732 R 78.8  1.1 594:49.68 apt-get install --yes --force-yes build-essential buil
 3870 root      15   0  105m  19m 7492 S 15.2  3.9  24:49.29 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0

---

