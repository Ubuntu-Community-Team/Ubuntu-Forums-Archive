---
title: "[SOLVED] SATA not mounting?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-12-27
so i got a seagate SATA 80 gig a few weeks back, and the SATA was malfunctioning at a BIOS lvl, untill xmas when i found my zoltrix nightingale soundcard was screwing everything up[USB died while it was pluged in] so now the drive shows up properly in BIOS[after replacing the sound card with a good one thats also newer] but linux wont mount it, saying something like "ATA validation ERRNO:(-19)" before loading boot files[i boot with no splash due to a mistake when editing my GRUB files]. and it doesnt show up in gparted
and no, i cant reload my OS, thats the whole reason i bought the drive, was to backup and reload my OS, at the same time installing winblows[dont want it, but do need it] and a few other distros] so if anyone has any idea how to fix this that would be great thanks
also, if it helps, my main drive i boot off of is a seagate 250 gig IDE drive, so no o havent gotten SATA working yet/before

---

### Post by blueridgedog on 2007-12-28
Do you currently have a dual boot system?  If so, can windows see the drive?

Can you post the output of:

sudo fdisk -lu

and

cat /proc/partitions

and

mount

Is gparted the only tool you have used to try and put a partition on it?

---

### Post by 99bluefoxx on 2007-12-30
no, i dont have a dual boot, ubuntu is my main at the moment, i was going to use this drive to backup data to install windows, so that my mp3 player wont 
keep breaking, and certane games will work
i tried a gutsy boot cd and it only saw my IDE drive, i think i need to replace my mobo and upgrade my PSU, mines only a 300w
sudo fdisk -lu
```
bluefoxx@azurE-prIDE:~$ sudo fdisk -lu

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   483861734   241930836   83  Linux
/dev/hda2       483861735   488392064     2265165    5  Extended
/dev/hda5       483861798   488392064     2265133+  82  Linux swap / Solaris
bluefoxx@azurE-prIDE:~$ 

```
and cat /proc/partitions
```

bluefoxx@azurE-prIDE:~$ cat /proc/partitions
major minor  #blocks  name

   3     0  244198584 hda
   3     1  241930836 hda1
   3     2          1 hda2
   3     5    2265133 hda5
bluefoxx@azurE-prIDE:~$ 

```
and yes, gparted is the only one i know how to use, so its all i have installed[only one i know of as well]
sorry to take so long to reply, been busy, my sansa e200 stoped recognizing on my computer, and the usb wont mount it, and now 650 out of 700 songs are gone from it, even though theyr still on the disk, and my dvd drive shreddded a gear, and then i steped on the metal case in the middle of the night and shredded my feet >>
life fails me once again...

---

### Post by blueridgedog on 2007-12-30
Well, it is clear from the output you posted that Ubuntu does not see your SATA hard disk.  That would imply that the disk is malfunctioning, that the data cable and /or power cable are not connected correctly or that your bios has SATA turned off.

Some things to test:

Check the cables
Check the bios to see that SATA is enabled
Try a different SATA port on the motherboard

---

### Post by 99bluefoxx on 2007-12-30
hehe, how stupid of me[i fail]
i forgot to plug in the drive XD
so i just installed gutsy, after re-pertitiioning my main drive
anyways, im gonna install the updates, then find out if i can import all my feisty account settings, if thats plausable
i know for a fact that the sata is enabled actually it will hang for a bit on startup at the detection of drives, so i prefere to leave the computer on and running various tasks, such as torrents or updates, i find it to be much more productive, lol

---

### Post by 99bluefoxx on 2008-04-03
ok i have this problem solved as of two months ago
ONE: my sata cable was a cheap piece of !@#$ that i found in a bargin bin for 50cents, and
TWO: my CPU was OCed from 2.93GHZ to 3.85GHZ causing general instability and also making the sata chip and other I/O chips malfunction in general[my webcam overvolted and blew the capacators preventing me from finding this until i unplugged everything]
moral of the story basically is dont push your CPU unless your gonna adequately cool the rest of your system[i actually singed my finger once just brushing the heatsink i put on the southbridge!]
~bfxx~

---

