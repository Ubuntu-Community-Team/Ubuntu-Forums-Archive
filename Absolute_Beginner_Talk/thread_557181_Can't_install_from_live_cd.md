---
title: "Can't install from live cd :|"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by mmisb on 2007-09-22
Ok, warning, I'm 100% linux virgin so please bear this is mind when replying ;x

Basically I am using the installer after booting live cd etc, and when it gets to the partion bit...well a) it only gives me 'manual' option b) I do not see any of my harddrives on the next page, obviously can't go on from there.

Er other stuff..all are NTFS, 1 was just formated for this...didn't come up either though.

'gparted' couldn't see my hard drives either. 

Oh and its 7.04 fiesty

Any help would be nice!

---

### Post by master_kernel on 2007-09-22
> **mmisb said:**
> Ok, warning, I'm 100% linux virgin so please bear this is mind when replying ;x

Basically I am using the installer after booting live cd etc, and when it gets to the partion bit...well a) it only gives me 'manual' option b) I do not see any of my harddrives on the next page, obviously can't go on from there.

Er other stuff..all are NTFS, 1 was just formated for this...didn't come up either though.

'gparted' couldn't see my hard drives either. 

Oh and its 7.04 fiesty

Any help would be nice!

EDIT: Sorry, I forgot you need to install this first:
```
sudo apt-get install ntfs-progs
```
```
sudo apt-get install ntfs-config
```

Try running in a terminal ( Applications > Accessories > Terminal ) this command:
```
sudo ntfsfix HARD DRIVE HERE
```

---

### Post by Pumalite on 2007-09-22
You probably have a laptop with a 'recovery partition' at the front of the drive that is causing all the trouble. That's my guess only.

---

### Post by mcduck on 2007-09-22
> **master_kernel said:**
> EDIT: Sorry, I forgot you need to install this first:
```
sudo apt-get install ntfs-progs
```
```
sudo apt-get install ntfs-config
```

Try running in a terminal ( Applications > Accessories > Terminal ) this command:
```
sudo ntfsfix HARD DRIVE HERE
```

Those are not needed for managing NTFS partitions, only for write access to them. Partitioning doesn't care what the file system is as it doesn't need to understand the data stored on the partition.

For the OP: what happens if you open the terminal and run 'sudo fdisk -l'? That should list all the disks and partitions on your system..

---

### Post by Pumalite on 2007-09-22
Get a Knoppix Live CD:[http://www.knoppix.org/](http://www.knoppix.org/) and a rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
And explore your system.

---

### Post by sailor2001 on 2007-09-22
if you are going to install.....download the alternate 7.04.....this is text based and I think faster and also gives you more control in the installation

---

### Post by mmisb on 2007-09-22
> **Pumalite said:**
> You probably have a laptop with a 'recovery partition' at the front of the drive that is causing all the trouble. That's my guess only.


Nope its desktop :|


> **master_kernel said:**
> EDIT: Sorry, I forgot you need to install this first:
```
sudo apt-get install ntfs-progs
```
```
sudo apt-get install ntfs-config
```

Try running in a terminal ( Applications > Accessories > Terminal ) this command:
```
sudo ntfsfix HARD DRIVE HERE
```

hum I did the later for all hard drive letters I use but I kept on getting the message

no such file/directory for all of them, in about 4 different ways each time.

though I hope this is because I didnt do the above? if not, eek i guess? :X

> **mcduck said:**
> Those are not needed for managing NTFS partitions, only for write access to them. Partitioning doesn't care what the file system is as it doesn't need to understand the data stored on the partition.



so, should I be 'eeking' or not? ;x

> 
For the OP: what happens if you open the terminal and run 'sudo fdisk -l'? That should list all the disks and partitions on your system..

mhm ok

> **Pumalite said:**
> Get a Knoppix Live CD:[http://www.knoppix.org/](http://www.knoppix.org/) and a rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
And explore your system.

'Was ist knoppix' ;S


Thanks for all the replys, I'm sure I'll get to the bottom of this somehow.

Is there anything else I should punch in the console/ do before I go under* ?

Or is this all can do for now

*takes like 20+mins for boot zzz

---

### Post by kay65535 on 2007-09-22
PowerQuest PartitionMagic is good at resizing NTFS partitions, but you have to install that on Windows (unless you can get hold of a boot CD with that on).

---

### Post by Linux_Man on 2007-09-22
Some desktops have "recovery" partions too. Make sure that your harddrive is connected. I know it seems stupid but it could be that a cable came loose, so make sure you can boot into windows.

---

### Post by Pumalite on 2007-09-22
What is KNOPPIX®?

KNOPPIX is a bootable Live system on CD or DVD, consisting of a representative collection of GNU/Linux software, automatic hardware detection, and support for many graphics cards, sound cards, SCSI and USB devices and other peripherals. KNOPPIX can be used as a productive Linux system for the desktop, educational CD, rescue system, or adapted and used as a platform for commercial software product demos. It is not necessary to install anything on a hard disk. Due to on-the-fly decompression, the CD can have up to 2 GB of executable software installed on it (over 8GB on the DVD "Maxi" edition).

---

### Post by mmisb on 2007-09-22
> **mcduck said:**
> 
For the OP: what happens if you open the terminal and run 'sudo fdisk -l'? That should list all the disks and partitions on your system..


Ok so I did that and it didnt do anything, did all the other ones to poke around also but no nice details telling me my harddrives are there at all in any shape or form.

Maybe you guys think I am running on another box but I'm not, same p.c and when I go windows all harddrives are found just fine (so no unplugged wire)

so basicaly ubuntu just doesn't recognise or find them at all- they are all internal and all working,

how can I fix this? I don't understand how KNOPPIX etc can help considering even if it can detect my hardware there is no way I can get this information to ubuntu as its 2 separate things right? unless there is some uber cache that stores infomation that isn't your harddrive that I'm not aware of

---

### Post by mmisb on 2007-09-23
bumP

:|

just to reiterate my problem..

gparted/ubuntu install not finding harddrives..

hence also ubuntu only gives 'manual option when install. '

---

