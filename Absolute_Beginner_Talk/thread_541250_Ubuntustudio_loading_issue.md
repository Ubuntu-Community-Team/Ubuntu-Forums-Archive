---
title: "Ubuntustudio loading issue"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by computercontrolled on 2007-09-02
Ok so i installed ubuntustudio...my current setup is ASUS P5W DH, P4 3.2 AND i have 4 hard drivers, 3 sata's and 1 ide...well i unplugged all my hard driver, only leaving connected the primary SATA driver in order to install ubuntustudio there. everything went ok, i installed,rebooted and everything worked well and fast. so i pluged all my hard drives again.

Primary SATA-Ubuntustudio
Secondary SATA-Windows XP
Third SATA-Storage driver (audio)
and the IDE river os connected to IDE 0.

The PC is set to start with the primary SATA drive. so i turned my PC on and Ubuntu started but now it got stucked on the logo sreen for ages, i rebooted like to times, and it started but taking a lot of time to do it. i woke up today, the same i spend 10 minutes trying to make ubuntu start but it stayed in the logo screen, with the progress bar at minimum, rebooted 1000 times pressed keyboard keys like an idiot and it started, again taking ages. 

Now i installed ubuntu without disconnecting the hard drivers, now i get the GRUB boot loader, clicked in ubuntu and the same, takes ages. I  noticed that when disconnecting the hard driver ubuntu laded quite fast, im sure it must be a hard driver issue, maybethe IDE drive, actually i have no idea please help.

---

### Post by shearn89 on 2007-09-04
okay - this sounds like a complicated problem, but i'll do what i can: when you get grub, hit escape, and change the boot commands, adding "nosplash" at the end, and removing the "quiet" option. This should give you loads of output. Post anything that looks relevant here.

---

