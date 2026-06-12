---
title: "Error Logging Tools (PC Hanging)"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by tonycm1 on 2008-02-06
Does Ubuntu 7.10 have any files that would give me system error logs so that I can find out why my system keeps hanging?

I just got a new PC and i'm thinking i might have shotty RAM or possibly even the CPU :(

My PC:
Ubuntu 7.10 x64
Athlon 5200+ dual core
Asus M2A-VM motherboard
2x1gig OCZ RAM

---

### Post by jordanmthomas on 2008-02-06
/var/log/ is a directory with logs
Enjoy :)

I think gnome has a log viewer that comes installed with ubuntu so you don't have to use gedit or a terminal if you don't want.

Also, the command 
```
dmesg
``` prints out a bunch of kernel messages and is often very useful in determining what's wrong.

Try booting memtest from grub and letting it run overnight to test your ram.

---

### Post by tonycm1 on 2008-02-06
Overnight!!! It takes THAT long?

---

### Post by jordanmthomas on 2008-02-06
Well, if your RAM is REALLY messed up, it might not take that long.
It's your choice how long you leave it going.  If you only run it for a few minutes the problem might not present itself though.

---

### Post by tonycm1 on 2008-02-09
Alright. I let the memtest go on for a full 24 hours and didn't find any errors.

The problem only seems to occur when I have many programs running (ie. MANY tabs open in several firefox windows)... which leads me to believe it's RAM related.

Does anyone have any suggestions ???????? :confused:

---

### Post by jordanmthomas on 2008-02-09
Well, if memtest didn't give any errors, it's most likely not your RAM.
Firefox for Linux isn't nearly as good as it is for Windows (I'm sure someone will disagree,  but whatever).  I know you have plenty of RAM, but firefox (ESPECIALLY when you have flash stuff open) really is pretty unstable

Does the whole system hang or just firefox?  As in, does ctrl-alt-backspace quit X and log you out?  If not, you can try to ping your computer to see if it's truly locked up or if it's just X.  If it's just X, it could be a number of things (not too major, luckily) but if your entire system is freezing there's a problem.

That's all I can think of at the moment.  Anyone else can feel free to add some suggestions in here.

---

### Post by tonycm1 on 2008-02-09
It's not isolated to firefox though... it's happened with other applications too :(

I thought it might have been a problem with my install disk when I installed Ubuntu, so I tried going onto my WinXP and WinVista partitions and the same problem occured....

Then, I tried booting off a live cd (ubuntu) and did a check CD for errors (came up with none) so i booted off the liveCD... after 20-30 mins of doing stuff in Ubuntu, system hung again

ohh, and by hung, i mean that it completely froze on me... not just the application, but all of the OS (in linux)... in windows (xp and vista), i get the blue screen of death (BSOD) and the system reboots.

It seems as though my computer runs fine as long as i don't "push it" by running many applications.... this, however, is a real nuissance.

This is why I originally posted because I wanted to find out if ubuntu has an equivalent of Windows "Event Viewer" to see if i can track down the root cause.... that way, I can "induce" the problem again and then reboot and see the log

???

---

### Post by jordanmthomas on 2008-02-10
You could maybe have a cooling issue.  Your CPU (or something else perhaps) may be getting too hot.

The equivalent of the system log in Windows is the stuff in /var/log
The program gnome-system-log will parse them and let you read them pretty easily, but I'm not sure that something like a CPU freeze would show up in the logs anywhere.

---

### Post by tonycm1 on 2008-02-10
I'll check the logs in a bit, but to be safe, i checked the temperatures... everything seems well below threshold (as shown below from PC Wizard 2008)

Hardware Monitoring :	ITE IT8716F
Voltage CPU :	1.25 V
+3.3V Voltage :	3.34 V
+5V Voltage :	5.04 V
+12V Voltage :	11.71 V
VTT :	3.34 V
VBAT :	3.23 V
Processor Fan :	3096 rpm
Chassis Fan :	10 rpm
FAN3 :	10 rpm
Processor Temperature :	23 °C
Processor Temperature (Core 1) :	29 °C
Processor Temperature (Core 2) :	30 °C
Mainboard Temperature :	31 °C
Power/Aux Temperature :	25 °C
ACPI Thermal Zone :	40 °C
 :	
Hard Disk Monitoring :	S.M.A.R.T
Hard Disk Temperature ST3320620A :	33 °C
Hard Disk Temperature WDC WD5000AAKS-00YGA0 :	37 °C

---

