---
title: "config a new drive"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by the.phantom on 2007-01-22
can someone please help with some cut and paste instructions
i an using edgy
i just installed a second hard drive
i used qtparted
and have it formatted and partitioned to be one 79 gig ex3 partition

i have read and tried what i found and got things a bit messed up 
all i want is to be able to find the drive and send data to it ( prime use is backup)as user
this is what i am showing now 

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4791    38483676   83  Linux
/dev/hda2            4792        4998     1662727+   5  Extended
/dev/hda5            4792        4998     1662696   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161   83  Linux

think i have the fstab a bit confused
so what should i have and how to enter it?

one post had me doing ctl x,ctl y,enter to save it
and when finished shuld have been a file called "storage" in the filesystem
well i have one but it is just the size of free space on hda

so if someone would feel sorry for this poor newbie and give me cut and paste you could make a friend for life !

mitch

---

### Post by xpod on 2007-01-22
[https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-80128df9c1c4215d74e3f016b5cd2c2352da247c)

This should help

---

### Post by taurus on 2007-01-22
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll to the end and add this line to it.

```
/dev/hdb1   /media/hdb1   ext3   defaults   0   1
```
Save it.  Now, create a mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by the.phantom on 2007-01-22
):P 

THANK YOU BOTH !
i will read and try to understand the link and i used the cut and past and all works well

**but it looks like it requires root to access it? i tried to put a file in it and it would not go ?**
it looks like it is mounted and i can open it from the desktop clicking the drive on the desktop and right clicking properties shows it for root?
what do i need for user to have "the power"

mitch doing his "snoopy happy dance"

and once i get a good backup maybe i can learn more and not panic all the time.
i get worried about a crash ( windows flashbacks) so really get worried when i make changes and have the system about the way i want it now 


oh did i say thank you ?

mitch

---

### Post by taurus on 2007-01-22
Okay, I assume your login name on your machine is **mitch**.  If it's not, then change it to whatever it is.

```
sudo chown -R **mitch**:**mitch** /media/hdb1
sudo chmod -R 755 /media/hdb1
```
Now, see if you can write to it without being root.

---

### Post by the.phantom on 2007-01-22
thank you again !!!!!!

now i can work on a good backup system and then won't panic when i am in root ;-DDD
appreciate the work , i really do !

---

