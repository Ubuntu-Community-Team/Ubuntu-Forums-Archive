---
title: "[SOLVED] ubuntu 7.04/winxp boot on two hard drives"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by bj218 on 2007-09-17
I have installed ubuntu 7.04 on one SATA HD and winxp on a second SATA HD. To date I have been runing the two systems by pluging in the HD power connector to the sys. I want to use. If I power up both HD's at the sme time will the boot sequence give me the option to select which sys. I want to boot?
Another thing I would like know is how do I backup ubuntu?

---

### Post by mlentink on 2007-09-17
Hmmm. That seems to me a bit awkward. Any reason why you didn't go for dual boot? 

For Backup I use Simple Backup, which is in the repo's, and suits me. There are others, though.

---

### Post by Hobo Joe on 2007-09-17
I'm a little confused, are you saying that you have Linux on one drive, and Windows on another, and you manually switch between them by plugging them in accordingly?

First, I didn't even know that was possible. Second, having the bootloader work if you plug them both ends depends on how you installed it. It may not work if you had one drive disconnected while you installed Ubuntu.

---

### Post by w4ett on 2007-09-17
I have that exact setup on one of my machines.....I use the boot device toggle (F11 on my machine) to select the drive to boot from....in this circumstance, Grub only controls the Ubuntu kernels and leaves the windows install completely alone.....The ubuntu/linux HDD is the primary and the windows is set to slave.

I installed each OS separately. with only 1 drive connected at install time.

---

### Post by dark_harmonics on 2007-09-17
Check out this post [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by CaptainInsaneO on 2007-09-17
I am running the exact same setup on my machine and have had no problems getting GRUB to dualboot both systems (through multiple Ubuntu installs to date). I actually think it works better having both operating systems on seperate hdds.

All you need to do to make this work is plug in both hard drives (power AND data cables) and reinstall grub.

---

### Post by bobpur on 2007-09-17
If I may put in my two cents, two OS's on two different drives is the best way to go. Don't get me wrong, I do have a machine here with both OS's on one drive and it works fine ... now. I meant to format a partition and formatted the whole drive wiping out a lot of work. Fortunately, it was all backed up on an external drive.
I've done dualboot on two SATA drives, two PATA drives and one OS on SATA and the other on a PATA drive (usually, Windows on SATA and Linux on PATA).
IMO,I just feel better installing one OS or formatting a drive knowing the other OS is out of the way

---

### Post by luptinpitman on 2007-09-17
As far as backing up, I like rsync.  You can also run Grsync if you want a graphical front end for it.  

[http://samba.anu.edu.au/rsync/](http://samba.anu.edu.au/rsync/)

[http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)

---

### Post by bj218 on 2007-09-19
Re dual boot on a single HD.  I did that about two weeks  ago and somthing I did wrong in ubuntu destroyed  both ubuntu and winxp, that is why I want  to use two different drives. How do I find REP's?

---

