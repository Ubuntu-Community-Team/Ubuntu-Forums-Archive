---
title: "3 install problems"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by yeago on 2007-05-29
Hey there, several problems installing Feisty:

1) All of my former /dev/hd* became /dev/sd*. I thought this was for SCSI devices? Ubuntu installer obviously became confused

2) GRUB of course doesn't work. Apparently the Ubuntu team decided to make GRUB the painful wisdom teeth of the project so that users will have an obstacle to overcome. At any rate, looking through menu.lst reveals several references to /dev/hdx instead (which doesn't exist of course, since my system made everything /dev/sdx). Why the install would do this is beyond me, and so is fixing it.

If the CD is not used, on boot grub simply goes:

GRUB  *HANG*

Changing the references in menu.lst doesn't work, and neither does the rescue option for fixing grub.

3) Ubuntu decided that my 320GB hard drive, which worked perfectly well an hour before the installation, shouldn't work. The device shows up in /dev/sda but the partition /dev/sda1 is not mountable. On boot there are clearly several problems with the device but I'm not sure which fix to perform, since I can't even mount the thing.

---

### Post by Happy_Man on 2007-05-29
1. Normal, part of Feisty kernel, don't sweat it, you'll be fine.

2. Not sure why.....

3. Is there something wrong with the partition? Is it corrupted?

---

### Post by Luis Fdo on 2007-05-29
Hi... I have a SATA drive and PATA drive, and ubuntu installed on PATA drive.  I have similar problem (grub wont run) and the problem was that my MB changes hd number after boot.  My SATA was recognized as sd1 drive, but for GRUB my SATA drive was hd1.  When I installed ubuntu for the first time, all references to my SATA drive was to hd0.  I changed all references to hd1 and it works.  Hope this help.

---

