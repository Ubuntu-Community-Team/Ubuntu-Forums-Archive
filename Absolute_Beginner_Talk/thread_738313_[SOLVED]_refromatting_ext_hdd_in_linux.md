---
title: "[SOLVED] refromatting ext hdd in linux"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-03-28
im trying to reformat my ext hdd which is currently loaded with ubuntu full os install plus grub. i want to wipe it clean so it can be read by windows again. I am going to load ubuntu 7.1 on it again in a way it can be run off anyones computer IN WINDOWS without rebooting. PLEAS helP:confused:

---

### Post by DBrocks on 2008-03-28
Are you dual-booting windows and linux? 
If you are, you should be able to format it from device manager in XP.

---

### Post by cisforcojo on 2008-03-28
[COLOR=Black]Have you tried gparted?[/COLOR]

---

### Post by N1N31NCHN41L5 on 2008-03-28
> **DBrocks said:**
> Are you dual-booting windows and linux? 
If you are, you should be able to format it from device manager in XP.

ok i dual boot ubuntu and windows yes - internally - this is a SEPERATE HDD (external - 40gig) that windows wont recognize. I just found a way to run ubuntu frrom a windows computer that is ccurrently running windows. but i gotta get windows to recognize the drive

---

### Post by cisforcojo on 2008-03-28
This should help you.
[http://ubuntuforums.org/showthread.php?t=435870](http://ubuntuforums.org/showthread.php?t=435870)

---

### Post by DBrocks on 2008-03-28
Does it show up as "Unallocated space", "Unformated" etc? that would be your linux partition.

---

### Post by N1N31NCHN41L5 on 2008-03-28
this computer runs xubuntu ONLY and has a 20 gig hdd 

here is my fdisk -l

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f545f54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2339    18787986   83  Linux
/dev/sda2            2340        2432      747022+   5  Extended
/dev/sda5            2340        2432      746991   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d02a533

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4665    37471581   83  Linux
/dev/sdb2            4666        4870     1646662+   5  Extended
/dev/sdb5            4666        4870     1646631   82  Linux swap / Solaris

---

### Post by cisforcojo on 2008-03-28
Yeah, I'd just use the link I gave you and reformat /dev/sdb to NTFS. Windows will recognize it.

EDIT: Scratch the link. I just quickly scanned it to see if it included NTFS. You need to use Windows to do it.

---

### Post by N1N31NCHN41L5 on 2008-03-28
> **cisforcojo said:**
> Yeah, I'd just use the link I gave you and reformat /dev/sdb to NTFS. Windows will recognize it.

NTFS or FAT 32???

---

### Post by N1N31NCHN41L5 on 2008-03-28
> **cisforcojo said:**
> Yeah, I'd just use the link I gave you and reformat /dev/sdb to NTFS. Windows will recognize it.

EDIT: Scratch the link. I just quickly scanned it to see if it included NTFS. You need to use Windows to do it.

or ntfs-3g????? so linux can read and write to it as well as windows?

---

### Post by Duck2006 on 2008-03-28
> **N1N31NCHN41L5 said:**
> NTFS or FAT 32???

Fat32 for a ext hdd drive.

---

### Post by cisforcojo on 2008-03-28
See, I have a FAT32 ext hdd and I'm currently waiting to convert it to NTFS (it's gotta be possible)!!!
It wasn't until I got all my stuff on it that I realized it's FAT32 (FAT32 limits you to a file size of 4gb which is terrible when you consider DVDs hold 4.3, also affects virtual machines since they tend to get a little large). I'd go with NTFS (ntfs-3g is a driver not a filesystem, linux will be able to read NTFS)

---

### Post by N1N31NCHN41L5 on 2008-03-28
josh@xubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  3.9G   13G  24% /
varrun                125M   84K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M  108K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   34M   91M  28% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1              36G  177M   34G   1% /media/disk
josh@xubuntu:~$ unmount /dev/sdb1
bash: unmount: command not found


it wont let me unmout it in the terminal - is it ok just to unmount it from the desktop and proceed???

---

### Post by cisforcojo on 2008-03-28
```
sudo umount /dev/sdb1
```

---

### Post by Duck2006 on 2008-03-28
Have you tried the live cd of gparted or parted magic?

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by cisforcojo on 2008-03-28
PartedMagic looks nice! 
I'm gonna try that on my ext hdd! w00t!

---

### Post by Duck2006 on 2008-03-28
I like pmagic better than gparted it have more utility on it to.

---

### Post by N1N31NCHN41L5 on 2008-03-28
> **cisforcojo said:**
> ```
sudo umount /dev/sdb1
```

josh@xubuntu:~$ sudo unmount /dev/sdb1
sudo: unmount: command not found
josh@xubuntu:~$

---

### Post by N1N31NCHN41L5 on 2008-03-28
and the link posted says for the ntfs a windows machine has to be used - but windows doesnt see this disk at all??????

I really wanna learn how to do this - but im gonna need REAL help and patience

---

### Post by Duck2006 on 2008-03-28
> **N1N31NCHN41L5 said:**
> and the link posted says for the ntfs a windows machine has to be used - but windows doesnt see this disk at all??????

I really wanna learn how to do this - but im gonna need REAL help and patience

How do you mean?

---

### Post by N1N31NCHN41L5 on 2008-03-28
> **Duck2006 said:**
> How do you mean?


Code:

fdisk /dev/sda

manualy you create the number of partitions you want and the size they will have (have in mind that the numbers
you will insert will be in the diad system, for example if you want 1GB, type +1024M). Try to have 2 or at least up to four partitions. If you want more, then some of them will be extended ones.
While you have typed the fdisk command if you type h you will find helpful information about the creation of partitions.

Now you can create the partitions. For my case:
1)
Code:

mkfs.ext3 -j dev/sda1 -L name of your partition up to 11 characters

2)
Code:

mkfs.vfat -F 32 -n name of your partition up to 11 characters dev/sda2

For the ntfs partition you have to use a windows machine.

Up to now we have partitioned the disk. YET you are still not able to write to the first partition (or if you prefer the extended one), unless you are root. In other words you cannot drug and drop items. This is because Linux systems are used also for security reasons.
In that case there are a couple of solutions. The first one is the following:






this is from my terminal - lost as to what to do now

Command (m for help): mkfs.vfat -F 32 Ubuntu 7.10 dev/sdb1
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help):

---

### Post by cisforcojo on 2008-03-30
> josh@xubuntu:~$ sudo unmount /dev/sdb1
sudo: unmount: command not found
josh@xubuntu:~$

You misread. It's 'umount', not 'unmount'.
Re: the help & patience, apologies if you find my help lacking.

Could you detail the steps you've taken in XP for reformatting your external? You should be using the 'Disk Utility' tool (Start -> Applications -> Utilities)
I found this out doing a google search for formatting either an unformatted external hdd or a mac os filesystem external hdd. Both are unreadable and I figured I'd get more hits than from ext3 to NTFS.
(Usually goes the other way around.)

EDIT: Noticed you've marked this solved. If you've solved it, please write what you did to help others who might read this thread.

---

### Post by N1N31NCHN41L5 on 2008-03-30
> **cisforcojo said:**
> You misread. It's 'umount', not 'unmount'.
Re: the help & patience, apologies if you find my help lacking.

Could you detail the steps you've taken in XP for reformatting your external? You should be using the 'Disk Utility' tool (Start -> Applications -> Utilities)
I found this out doing a google search for formatting either an unformatted external hdd or a mac os filesystem external hdd. Both are unreadable and I figured I'd get more hits than from ext3 to NTFS.
(Usually goes the other way around.)

EDIT: Noticed you've marked this solved. If you've solved it, please write what you did to help others who might read this thread.

Reformatting my external, that was as simple as installing GParted. Once installed simply typin g sudo gp[arted in the terminal and all options were plain and easy to follow, even for a first time user. Only thing you can't do is reformat into NTFS, but you can do FAT 32 which is then recognized by Window's "Disk Utilkity" for conversion to NTFS if desired. I've never had any probl;ems with FAT32 regardless of file size so I left it at that. If you are using Gparted in Linux you will EASILY be able to convert ext3 to FAT32, and if NTFS is your final outcome desire, can make the final transistion smoothly.


To install GParted

Open a terminal window and type in:
sudo apt-get install gparted

After that simply type sudo gparted in the terminal to open and run.

---

### Post by N1N31NCHN41L5 on 2008-03-30
EDIT: Universe and Multiverse repositories must be enabled in software sources for the installation of GParted.

---

### Post by N1N31NCHN41L5 on 2008-03-30
This link here will walk you through conversion from FAT to NTFS:

[http://technet.microsoft.com/en-us/library/bb456984.aspx](http://technet.microsoft.com/en-us/library/bb456984.aspx)

---

