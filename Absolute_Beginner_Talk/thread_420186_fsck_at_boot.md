---
title: "fsck at boot"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Pisi-Deff on 2007-04-23
I installed feisty 2 days after it came out (dual boot with WinXP) and I'm blinded by it's beauty :D
The only problem is that at every boot fsck starts checking and hides the boot splash image. I never get to see the loading bar go to the end.
Is that a bug or does it have to run every time and ruin my splash image? And is there a way to solve it?

---

### Post by Cypher on 2007-04-23
How are you shutting down the PC? If you do a clean shutdown without anything left hanging, then the FSCK should not  happen on every boot but rather at set intervals of like 40 mounts (usually 40 boots or 40 days) or something..

Regards

---

### Post by Pisi-Deff on 2007-04-23
> **Cypher said:**
> How are you shutting down the PC? If you do a clean shutdown without anything left hanging, then the FSCK should not  happen on every boot but rather at set intervals of like 40 mounts (usually 40 boots or 40 days) or something..

Regards
I press the big red shutdown button (top tab thing) and choose Shut Down. Then it unloads for about 25 sec and turns off...
Thanks for the quick answer. :)

---

### Post by Pisi-Deff on 2007-04-24
Bump

---

### Post by xyz on 2007-04-24
Hi,
In a terminal, copy/paste:
 ```
sudo gedit /etc/default/rcS 
```
Now change the FSCKFIX line to the following:

FSCKFIX=yes or no if you don't want it to run

Should look like this:
> ht@luser:~$ cat /etc/default/rcS 
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no
ht@luser:~$ 

There's also a command line to set check disk options at boot but it just won't come to mind right now.

---

### Post by xyz on 2007-04-24
got it now:
```
sudo tune2fs -c 50 /dev/hdx
```
This means it'll check your disk at the 50th reboot. Change the value to what you want.
Also modify the  x  in  hdx  to what corresponds to yours.
To find out, run as root:
```
fdisk -l
```
in a terminal.
Hope this helps. Let us know....

---

### Post by Pisi-Deff on 2007-04-24
```
eerik@Eerik-Ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3837    30820671    7  HPFS/NTFS
/dev/sda2            7110       38913   255465630    f  W95 Ext'd (LBA)
/dev/sda5           14683       38913   194635476    b  W95 FAT32
/dev/sda6            7111       10374    26218048+  83  Linux
/dev/sda7           10375       14290    31455238+  83  Linux
/dev/sda8           14291       14682     3148708+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
That file looks like this:
```
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no

```
And when I typed sudo tune2fs -c 50 /dev/sda
It said:
```
eerik@Eerik-Ubuntu:~$ sudo tune2fs -c 50 /dev/sda
tune2fs 1.40-WIP (14-Nov-2006)
tune2fs: Bad magic number in super-block while trying to open /dev/sda
Couldn't find valid filesystem superblock.

```

Edit:// I forgot to put in the number after sda... Now it said, that it set the maximal mount count to 50.
I'll reboot to see what happens.

---

### Post by xyz on 2007-04-24
You seem to have forgotten a number here: /dev/sdaX
The X must correspond to your Linux partition which you want checked only at the 50th reboot.

---

### Post by Pisi-Deff on 2007-04-24
ps: read the edit of my last post :P
Anyway, I just rebooted and it still did the fsck.

---

### Post by xyz on 2007-04-24
According to your  "fdisk -l" you have 2 Linux partitions. Does it by any chance run the check on the partition you didn't set disk check options?

---

### Post by Pisi-Deff on 2007-04-24
The first is a 25GB /home partition and the second is a 30GB root partition. I used the command on both of em.

---

### Post by xyz on 2007-04-24
Try this:
Run ```
sudo tune2fs -c 0 -i 0
``` to disable interval checks.

And to quote the paranoid man page:

> It is strongly recommended that either -c (mount-count-depen&#8208;
dent) or -i (time-dependent) checking be enabled to force peri&#8208;
odic full e2fsck(8) checking of the filesystem. Failure to do
so may lead to filesystem corruption due to bad disks, cables,
memory, or kernel bugs to go unnoticed until they cause data
loss or corruption.

Also you can skip the check with CTRL + C. Then press CTRL + D to resume bootup.

---

### Post by mcduck on 2007-04-24
Instead of completely disabling fsck, it would be better to just disable it for those partitions you don't want to check, in this case your windows partitions. Just edit /etc/fstab and change the last number in those partitions entry lines to 0.

I bet disabling fsck for windows partitions will solve your problem.

(By the way, tune2fs works only for Ext2/Ext3 partitions..)

---

### Post by Pisi-Deff on 2007-04-24
> **mcduck said:**
> Instead of completely disabling fsck, it would be better to just disable it for those partitions you don't want to check, in this case your windows partitions. Just edit /etc/fstab and change the last number in those partitions entry lines to 0.

I bet disabling fsck for windows partitions will solve your problem.

(By the way, tune2fs works only for Ext2/Ext3 partitions..)
# /dev/sda5
UUID=4621-4905  /media/Files    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=DC5C6FB45C6F885A /media/WinXP    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

The upper is a FAT32 storage partition and the other is WinXP.
What do I have to remove and do I have to remove it from both?

---

### Post by mcduck on 2007-04-24
> **Pisi-Deff said:**
> # /dev/sda5
UUID=4621-4905  /media/Files    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=DC5C6FB45C6F885A /media/WinXP    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

The upper is a FAT32 storage partition and the other is WinXP.
What do I have to remove and do I have to remove it from both?
Just change the last number on both those lines from '1' to '0' and reboot :)
```
# /dev/sda5
UUID=4621-4905  /media/Files    vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda1
UUID=DC5C6FB45C6F885A /media/WinXP    ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```

I don't know why windows partitions sometimes have '1' in Ubuntu, as in no case should any other partition than / have '1', all other partitions that are checked should have '2' (to check them after /). But in my opinion running fsck for windows partitions is no use anyway, and as they are not able to store information about when they were checked last time I recommend disabling fsck on them completely by using a '0'.

So, '1' is for root partition, '2' is for all other partitions you wish to check, and '0' disables fsck on that partition.

---

### Post by Pisi-Deff on 2007-04-24
> **mcduck said:**
> Just change the last number on both those lines from '1' to '0' and reboot :)
```
# /dev/sda5
UUID=4621-4905  /media/Files    vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda1
UUID=DC5C6FB45C6F885A /media/WinXP    ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```

I don't know why windows partitions sometimes have '1' in Ubuntu, as in no case should any other partition than / have '1', all other partitions that are checked should have '2' (to check them after /). But in my opinion running fsck for windows partitions is no use anyway, and as they are not able to store information about when they were checked last time I recommend disabling fsck on them completely by using a '0'.

So, '1' is for root partition, '2' is for all other partitions you wish to check, and '0' disables fsck on that partition.
Thanks a lot to all of you :D
This finally solved it and I also learned a few new commands :P

---

### Post by NPuter on 2007-04-25
Thanks this really helped a lot
this could be made into a good how-to:) 
all along I thought that this was something I had to live with

---

