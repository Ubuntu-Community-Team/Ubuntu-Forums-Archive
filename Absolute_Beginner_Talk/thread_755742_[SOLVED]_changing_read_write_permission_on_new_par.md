---
title: "[SOLVED] changing read write permission on new partition"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by tropdoug on 2008-04-15
Boy there is a mountain of stuff to learn.


OK I repartitioned my windows 80gb disk to 50gb ext 3 and the rest for windows. I used Gparted from a live cd. All went great, I have a new ext3 partition to store my extensive music collection on. 
However I cannot read write to it. It appears under Places > Computer [COLOR=Blue]> 44.7 gb disk-1[/COLOR] and I can open it to show a single folder [COLOR=Blue]lost+found [COLOR=Black]if I try to open the folder it wont let me, and I cannot copy my music folder to it.

so it obviously mounts when I boot, so what do I do to change the owner permissions and give myself the read write permissions I need? Attached a number of screen shots if they are any use. 

Tnanks
[/COLOR][/COLOR]

---

### Post by marufaberlin on 2008-04-15
Please post results of 
```
sudo cat /etc/fstab
```

Try ```
gksu nautilus
``` and change permissions there, but I doubt that'll help.

---

### Post by marufaberlin on 2008-04-15
P.S.: Have a look at your 2nd screenshot, what it shows :D

---

### Post by marufaberlin on 2008-04-15
Can you post screenshots of the Drive and Volume Tabs?

---

### Post by tropdoug on 2008-04-15
Ooops LOL 
 here is what it should have been and the req outputs

douglas@desktop:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=7e72d20f-1ce6-4265-9533-0e15ca9abf9a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=79dd635c-adee-4702-a5e0-b4cc9ace54a5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
douglas@desktop:~$ 

**[COLOR=Black] This is what fdisk gave me, and the partition I am trying to change is highlighted in blue (I think, I am colour blind, ROFLMAO)[/COLOR]**

douglas@desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4eab4176

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3888    31230328+   7  HPFS/NTFS
[COLOR=Blue]/dev/sda2            3889        9729    46917832+  83  Linux[/COLOR]

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3657373

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extended
/dev/sdb5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x170a8ae2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    c  W95 FAT32 (LBA)
Note: sector size is 2048 (not 512)

Disk /dev/sdd: 2038 MB, 2038171648 bytes
32 heads, 32 sectors/track, 971 cylinders
Units = cylinders of 1024 * 2048 = 2097152 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         971     1988518    6  FAT16


Using gksu nautilus, I cannot get high enough up the tree. ( I think thats what its called is it? see I am keen to learn the lingo too.) 

Douglas

---

### Post by tropdoug on 2008-04-15
here is the drive and volume shots

---

### Post by tropdoug on 2008-04-15
Its odd, but I thought that cos it is an ext3 partition and I created it, I would simply be able to use it right out of the bocks. Oh well.

---

### Post by marufaberlin on 2008-04-15
try putting your disk in fstab. Then change ownership of the folder you mount in to yourself and give 644 permissions.

---

### Post by quinnten83 on 2008-04-15
> **marufaberlin said:**
> try putting your disk in fstab. Then change ownership of the folder you mount in to yourself and give 644 permissions.

I think he is going to need some instructions on doing that....!

---

### Post by tropdoug on 2008-04-15
Yup your right quinnten83, I would nbeed instruction. 

But before I do that I was in a terminal thinking, (scarey) and I decided to do a bit of digging. this is what I came up with 

douglas@desktop:/media$ ls -l
total 72
lrwxrwxrwx  1 root    root     6 2008-04-02 20:31 cdrom -> cdrom0
drwxr-xr-x  2 root    root  4096 2008-04-02 20:31 cdrom0
drwx------  4 douglas root 16384 1970-01-01 10:00 disk
[COLOR=Blue]drwxr-xr-x  3 root    root  4096 2008-04-13 20:22 disk-1[/COLOR]
drwxr-xr-x 47 root    root 32768 1970-01-01 10:00 seagate
douglas@desktop:/media$ sudo 

so looking at that, wont I have to first change the ownership, and then change the permissions?

---

### Post by tropdoug on 2008-04-15
Ok done it, and it was a little simple after all.

Once I realised that the permissions were in /media/disk-1
I used sudo chown as below

douglas@desktop:/media$ sudo chown douglas disk-1
douglas@desktop:/media$ ls -l
\total 72
lrwxrwxrwx  1 root    root     6 2008-04-02 20:31 cdrom -> cdrom0
drwxr-xr-x  2 root    root  4096 2008-04-02 20:31 cdrom0
drwx------  4 douglas root 16384 1970-01-01 10:00 disk
drwxr-xr-x  3 douglas root  4096 2008-04-13 20:22 disk-1
drwxr-xr-x 47 root    root 32768 1970-01-01 10:00 seagate


then once I was the owner i simply did 

gksudo nautilis, and changed the permissions via the GUI. 

and now I have 

douglas@desktop:/media$ ls -l
total 72
lrwxrwxrwx  1 root    root        6 2008-04-02 20:31 cdrom -> cdrom0
drwxr-xr-x  2 root    root     4096 2008-04-02 20:31 cdrom0
drwx------  4 douglas root    16384 1970-01-01 10:00 disk
drwxrwx---  4 douglas douglas  4096 2008-04-15 21:56 disk-1
drwxr-xr-x 47 root    root    32768 1970-01-01 10:00 seagate
douglas@desktop:/media$ 


Thanks for the help marufaberlin it was greatly appreciated, now I can go to bed. 

[COLOR=Blue]*Have a great day everyone, life is wonderful, just look around. *[/COLOR]

---

