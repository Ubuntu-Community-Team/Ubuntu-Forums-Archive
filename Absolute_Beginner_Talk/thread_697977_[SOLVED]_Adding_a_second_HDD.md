---
title: "[SOLVED] Adding a second HDD"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by kennster on 2008-02-15
i just got a new 500gig stat HDD and dont know how to get it working ... any ideas?

---

### Post by dcstar on 2008-02-15
> **kennster said:**
> i just got a new 500gig stat HDD and dont know how to get it working ... any ideas?

[http://ubuntuforums.org/showpost.php?p=4212634&postcount=3](http://ubuntuforums.org/showpost.php?p=4212634&postcount=3)

---

### Post by MasterJS on 2008-02-15
is it a SATA drive or IDE?

---

### Post by kennster on 2008-02-15
> **MasterJS said:**
> is it a SATA drive or IDE?

SATA and i downloaded and  gparted "i think" i cant find it to even try useing that 

i did this to install 
```
sudo apt-get install gparted
```

---

### Post by stevejesus on 2008-02-15
How do you plan to use the drive?  By that I mean, do you want just one big partition, or something else.

---

### Post by MasterJS on 2008-02-15
in a terminal type ```
sudo fdisk -l
``` This will list the hard drives and partitions on and connected to your system. Show it here when you've done it.

---

### Post by kennster on 2008-02-15
> **stevejesus said:**
> How do you plan to use the drive?  By that I mean, do you want just one big partition, or something else.

lol um as a media drive for music games "WoW" picks ext, my HDD now is a WD 10,000rpm raptor 120gig and whell 120gigs gets full fast from misanalysed

---

### Post by kennster on 2008-02-15
> **MasterJS said:**
> in a terminal type ```
sudo fdisk -l
``` This will list the hard drives and partitions on and connected to your system. Show it here when you've done it.

```
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a382358

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17495   140528556   83  Linux
/dev/sda2           17496       18241     5992245    5  Extended
/dev/sda5           17496       18241     5992213+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdd: 65 MB, 65486848 bytes
4 heads, 32 sectors/track, 999 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1000       63936    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1023, 3, 32) logical=(999, 0, 32)

```

---

### Post by MasterJS on 2008-02-15
Okay, see there is your problem. There is no MBR on that disk. There is no existing partition that you can work with. Try downloading GParted to create a partition. Just to tell you how i got that info, your disk is SDB. So basically your system is telling you what i just told you

---

### Post by kennster on 2008-02-15
> **MasterJS said:**
> Okay, see there is your problem. There is no MBR on that disk. There is no existing partition that you can work with. Try downloading GParted to create a partition. Just to tell you how i got that info, your disk is SDB. So basically your system is telling you what i just told you

yes HDD just arived ups about 30min ago so i would hope nuttins been installed lol

but i think i have GParted installed ware would i locate it?

---

### Post by antisocialist on 2008-02-15
this shows me that most likely /dev/sdb is your new hard drive
if you installed ubuntu from a livecd then boot that up and type sudo gparted
if not... well... get the gparted livecd lol

---

### Post by kennster on 2008-02-15
> **antisocialist said:**
> this shows me that most likely /dev/sdb is your new hard drive
if you installed ubuntu from a livecd then boot that up and type sudo gparted
if not... well... get the gparted livecd lol

i got Gparted to run 
```
sudo gparted
```

and now its scanning drive or w,e it dose but its takeing a bit... after that i might be back cuz might not know what i am doing lol

---

### Post by kennster on 2008-02-15
ok ive tryed running sudo gparted a few times and it poped up saying unable to mount flopy drive

---

### Post by MasterJS on 2008-02-15
But does it mount your hard drives? At the top of the GParted screen, there should be a dropdown area to choose between hard drives. You should choose sdb.

---

### Post by kennster on 2008-02-15
bump still no fix for me :(

---

### Post by kennster on 2008-02-16
i need to be log in as root how do i do so?

---

### Post by aysiu on 2008-02-16
> **kennster said:**
> i need to be log in as root how do i do so?
You don't need to log in as root. Read this:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by mattismyname on 2008-02-16
Applications->Accessories->Terminal
Type in "sudo su", then your password.  That terminal will now be logged in as root.

Root is the equivalent of the "administrator" account on windows.

---

### Post by kennster on 2008-02-16
> **mattismyname said:**
> Applications->Accessories->Terminal
Type in "sudo su", then your password.  That terminal will now be logged in as root.

Root is the equivalent of the "administrator" account on windows.

my probelm is i just instaled a second HDD  and cant save nuttin to it cuz it ses olny root can chage stuff  and i cant save files thare cuz i dont have permion...

---

### Post by kennster on 2008-02-16
> **aysiu said:**
> You don't need to log in as root. Read this:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

i went thare and didnt realy understnad what to read...? sry and btw im tryin to set up a new HDD so i can read and wright stuff on it cuz olny root has acess to it now :(

---

### Post by aysiu on 2008-02-16
> **kennster said:**
> i went thare and didnt realy understnad what to read...? sry and btw im tryin to set up a new HDD so i can read and wright stuff on it cuz olny root has acess to it now :(
Root has nothing to do with it.

One of these links should help.

For NTFS or FAT32:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

For Ext3:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

