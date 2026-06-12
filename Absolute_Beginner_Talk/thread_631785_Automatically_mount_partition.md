---
title: "Automatically mount partition"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by OlyPerson on 2007-12-04
Ok, so every time I go into RythmeBox to listen to my music I have to first mount the Windows partition and then I have to wait around 10-15 minutes for all the songs to load, at least I think that's what it's doing.  So I have two questions:

1) Will automatically mounting the partition work to speed it up or is the problem elsewhere?

2) In noob terminology, how do I automatically mount a partition (my XP one) on start up?

I've looked in other places for this but they didn't address my problem and I didn't understand them.  Thanks in advance!

---

### Post by fenian on 2007-12-04
Follow the guide[ here.]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by OlyPerson on 2007-12-04
The part with the backup troubles me.  I don's have enough disk space to back up my Windows partition, is that what that step is doing?

---

### Post by OlyPerson on 2007-12-04
Also, I did the ```
sudo nano /etc/fstab
``` and there was no NTFS partition to be seen, although there was one when I typed in ```
sudo fdisk -l
```
What's up with that?

My sudo fdisk -l:
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        6703    53809717+   7  HPFS/NTFS
/dev/sda3            6704        9595    23229990   83  Linux
/dev/sda4            9596        9726     1052257+   5  Extended
/dev/sda5            9596        9726     1052226   82  Linux swap / Solaris

Disk /dev/sdb: 262 MB, 262144000 bytes
16 heads, 32 sectors/track, 1000 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1000      255975+   6  FAT16
```

My sudo nano /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c356e0b0-3384-401e-9209-d7dbdf4d9c71 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6b54039d-ad55-4867-be3a-eaab6330e533 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by Paqman on 2007-12-04
/etc/fstab is the File System TABle. The reason your drive isn't mounted at boot is *because* it's not listed in fstab.

You'll need to add an entry for your NTFS partition manually (yuck). The fdisk command tells you that your NTFS partition is sda2, so go ahead and add a new entry to fstab reflecting that.

The backup it mentions is a backup of the fstab file only, which will only be a few kilobytes. It's really important to backup fstab before hacking it manually, as cocking it up can leave your system in a proper mess.

You can mount your partition to a folder in the /media directory, if you like. Then it'll automatically show up on the desktop.

---

### Post by OlyPerson on 2007-12-04
> **Paqman said:**
> /etc/fstab is the File System TABle. The reason your drive isn't mounted at boot is *because* it's not listed in fstab.

**You'll need to add an entry for your NTFS partition manually (yuck). The fdisk command tells you that your NTFS partition is sda2, so go ahead and add a new entry to fstab reflecting that.**

The backup it mentions is a backup of the fstab file only, which will only be a few kilobytes. It's really important to backup fstab before hacking it manually, as cocking it up can leave your system in a proper mess.

You can mount your partition to a folder in the /media directory, if you like. Then it'll automatically show up on the desktop.

Umm, how do I go about doing that?

---

### Post by Paqman on 2007-12-04
> **OlyPerson said:**
> Umm, how do I go about doing that?

Heheh, by reading the Psychocats guide!

If you've created your mount point, open up fstab for editting:

```
sudo nano /etc/fstab
```

Add a new entry (in with the other partitions is tidiest):

```
/dev/sda2 /*change_this_to_your_mount_point* ntfs nls=utf8,umask=0222 0 0
```

Ctrl-X > Y > Enter.

To mount it straight away:

```
sudo mount -a
```

If you chose a mount point in /media it'll pop up on the desktop. Otherwise you can just browse to where you mounted it.

---

### Post by OlyPerson on 2007-12-04
Oh yay!  That worked!  Awesome, thanks.

---

### Post by Paqman on 2007-12-04
No probs! ;)

---

