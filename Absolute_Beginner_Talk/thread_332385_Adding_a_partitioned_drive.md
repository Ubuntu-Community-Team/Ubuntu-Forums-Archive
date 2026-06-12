---
title: "Adding a partitioned drive"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by tordan on 2007-01-06
Hello,

This is the second time I have tried to mount this drive. This time I have been using it for a week and have files on it I would like to save.

I had just gotten my Edgy Eft up and working properly when my primary hard drive fried and I had to procure another.

The new drive is 30 gigs and the one I would like to mount is 60 gigs. How do I do I mount this drive to the newly installed Ubuntu without loosing the information.

I don't understand the terminal code very well, so please take me step by step,

Anyone?

---

### Post by logos34 on 2007-01-06
Let's have look at your drives and partitions.

Open a terminal and type:
> sudo fdisk -l
cat /etc/fstab
ls /dev/disk/by-uuid/ -alh

Copy and post it

---

### Post by tordan on 2007-01-06
desktop:~$  sudo fdisk -l
Password:

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         637     5116671   83  Linux
/dev/hda2             638        1808     9406057+  83  Linux
/dev/hda3   *        1809        3569    14145232+  83  Linux
/dev/hda4            3570        3649      642600    5  Extended
/dev/hda5            3570        3649      642568+  82  Linux swap / Solaris

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7297    58613121   83  Linux


Thanks for the help.
I see it recognizes the 60 gig, but where do we go from here?

---

### Post by taurus on 2007-01-06
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Add the following line to the end of it.

```
/dev/hdb1   /media/hdb1   ext3   defaults   0   1
```
Save it.  Then, create a new mount point for it and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by tordan on 2007-01-06
It gave me this message and opened fstab.

(gedit:5596): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

if thats okay, am I entering:
/dev/hdb1   /media/hdb1   ext3   defaults   0   1

...in the fstab or the terminal?

---

### Post by taurus on 2007-01-06
Even with that warning, does gedit open at all?

---

### Post by tordan on 2007-01-06
fstab (/etc)- gedit opened and reads:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=4da888b5-4f35-4dea-979a-55b44ece471c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d6004c3d-38ed-43e6-8d4d-674ba10dd3a6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2007-01-06
Good.  Now, just continue with my Post #4 from above.

---

### Post by tordan on 2007-01-06
Next code in fstab or in the terminal?

---

### Post by taurus on 2007-01-06
Add this line to the end of /etc/fstab.

```
/dev/hdb1   /media/hdb1   ext3   defaults   0   1
```
Then save it.  Now, run

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by tordan on 2007-01-06
it displays this after that last set of codes:
mkdir: cannot create directory `/media/hdb1': File exists

---

### Post by taurus on 2007-01-06
Then you don't need to create it since it's already there.  Now, just mount it...

```
sudo mount -a
df -h
```

---

### Post by tordan on 2007-01-06
yes.

---

### Post by taurus on 2007-01-06
So everything is good now!

---

### Post by tordan on 2007-01-06
I have to restart now and it should be working?

---

### Post by taurus on 2007-01-06
Actually, you don't have to but can reboot if you want.

---

### Post by tordan on 2007-01-06
How do I access it?
I went to Places>Computer and it is not listed and no space has been added (as far as I can tell).

---

### Post by taurus on 2007-01-07
```
ls -la /media/hdb1
```
Or you can use **nautilus** and navigate to /media/hdb1...

---

### Post by tordan on 2007-01-07
Hoopty-loo!!

It werkedid!

Thank you kindly, It is there on my desktop after restarting. All appears to be working.

Yer awesome. Have a good night.

---

### Post by taurus on 2007-01-07
Yes, there should be an icon on your Desktop for it...

---

