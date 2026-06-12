---
title: "How do I install a slave Hard Drive?"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by MaxGunnar on 2007-10-07
I got the drive physically installed and Ubuntu sees it but it won't let me write to it.   


   "You do not have permission to write to this folder"    

how to I get access to it?

---

### Post by Pumalite on 2007-10-07
If it is formatted ntfs, you need to install ntfs-3g.

---

### Post by MaxGunnar on 2007-10-07
I loaded Ubuntu on that as well thinking that will format it so I can write to it,   didn't work,

---

### Post by Pumalite on 2007-10-07
Maybe is a matter of permissions. Where is that drive mounted?. Post:
sudo fdisk -lu

---

### Post by ryanVickers on 2007-10-07
In the mean time, viewing it as root (gksudo nautilus) will work (in theory, unless it's something other than permissions)

---

### Post by MaxGunnar on 2007-10-07
> **Pumalite said:**
> Maybe is a matter of permissions. Where is that drive mounted?. Post:
sudo fdisk -lu

yea that's what I'm thinking,  how do I set up permissions?  I open the tabs but it won't let me

---

### Post by Pumalite on 2007-10-07
I need to know fdisk output and where the drive is mounted to help you. Is it /media/disk?

---

### Post by MaxGunnar on 2007-10-07
> **Pumalite said:**
> I need to know fdisk output and where the drive is mounted to help you. Is it /media/disk?

> erika@erika-desktop:~$ fdisk output 

Unable to open output
erika@erika-desktop:~$ fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
erika@erika-desktop:~$ 



thats what it says

---

### Post by Pumalite on 2007-10-07
It's:
sudo fdisk -lu

---

### Post by MaxGunnar on 2007-10-07
> **Pumalite said:**
> It's:
sudo fdisk -lu

> Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    56115044    28057491   83  Linux
/dev/hda2        56115045    58621184     1253070    5  Extended
/dev/hda5        56115108    58621184     1253038+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   149838254    74919096   83  Linux
/dev/hdb2       149838255   156296384     3229065    5  Extended
/dev/hdb5       149838318   156296384     3229033+  82  Linux swap / Solaris
erika@erika-desktop:~$ 



I'm trying to get to the 80 gig HD

---

### Post by Frak on 2007-10-08
```
sudo aptitude install gparted
```

Then startup gParted and format the drive to Ext3

You are most likely getting an issue with an unpartitioned drive.

---

### Post by MaxGunnar on 2007-10-08
Nothing worked    :(    so I upgrade to 7.10 to see if they fixed that issue,    

WoooooooHoooooo   Works great now  7.10 fixed the prob

---

### Post by Paqman on 2007-10-08
> **MaxGunnar said:**
> 
WoooooooHoooooo   Works great now  7.10 fixed the prob

I'm guessing that's because Gutsy supports writing to NTFS.

That's because Gutsy is awesome, by the way :)

---

### Post by ryanVickers on 2007-10-08
Could you see [my questions about it]("http://ubuntuforums.org/showthread.php?t=570990")?...

---

