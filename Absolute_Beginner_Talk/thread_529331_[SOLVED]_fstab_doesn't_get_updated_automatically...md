---
title: "[SOLVED] fstab doesn't get updated automatically..."
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by chatterjee on 2007-08-19
fstab doesn't get updated automatically.I formatted my hardisk with Gparted but it doesn't  reflect on fstab.I formatted it in ext3 while fstab reflects ntfs!As a result of that the volumes don't get mounted on boot up.Please tell me the way how it should be done?Should I have to do it manually?

Fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdb1
UUID=f4b726d6-76cf-438f-9b6a-4afdc6b15c4f / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1
UUID=F4741FCE741F928A /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5
UUID=64BC9896BC986478 /media/hda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda6
UUID=8240-F37E /media/hda6 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hdb5
UUID=68E9-02F3 /media/hdb5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hdb7
UUID=d7637bbe-157f-4fc3-b8fd-3931160a45a1 /media/hdb7 ext3 defaults 0 2
# /dev/hdb6
UUID=3a5095da-41f3-4e4e-a768-0c24bf333572 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

---

### Post by Ek0nomik on 2007-08-19
I'd just edit your fstab yourself.

```
sudo nano /etc/fstab

*or*

gksu gedit /etc/fstab
```

Then I would just take the portion dealing with EXT3 already in your fstab file and replace it with your current NTFS entry.

Make sure you create a directory for where you want it to be mounted.  Example:

```
mkdir /media/MyDrive
```

and then put this path in the relevant fstab entry.

---

### Post by schorsch on 2007-08-19
The file /etc/fstab is not updated by gparted; you have to edit it manually.
```
gksu gedit /etc/fstab
```

---

### Post by chatterjee on 2007-08-19
I'll be greatly helped if you please say what should be the replacement of the following two lines.

# /dev/hda1
UUID=F4741FCE741F928A /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5
UUID=64BC9896BC986478 /media/hda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

---

### Post by schorsch on 2007-08-19
To mount them to the same mountpoints you should change the mentioned lines to look like this:
```

# /dev/hda1
UUID=F4741FCE741F928A /media/hda1 ext3 defaults 0 1
# /dev/hda5
UUID=64BC9896BC986478 /media/hda5 ext3 defaults 0 1

```

---

### Post by chatterjee on 2007-08-19
No,it's not working.Giving an error message:

WARNING: bad format on line 1 of /etc/fstab
fsck.ext3: Unable to resolve 'UUID=F4741FCE741F928A' 
fsck.ext3: Unable to resolve 'UUID=64BC9896BC986478' 
open UUID=8240-F37E:No such file or directory

---

### Post by schorsch on 2007-08-19
Hmm, well, as you have formatted the partitions the UUIDs may have changed. So there are two options:

1. Replace "UUID=F4741FCE741F928A" with "/dev/hda1" and "UUID=64BC9896BC986478" with /dev/hda5

2. You could run the following command
```
 sudo vol_id -u /dev/hda1
``` and change the UUID accordingly. Do this for /dev/hda5, too.

Could you please post your actual /etc/fstab again as there seems to be an error in line 1 regarding your last post?

---

### Post by chatterjee on 2007-08-19
Thank you for your kind effort.

/dev/hda1 gets mounted automatically but I don't know why /dev/hda5 is not working.The above mentioned command works well for /dev/hda1 but when applied on /dev/hda5 it gives:
> /dev/hda5: error open volume
So I tried using /dev/hda5 instead of the UUID.But on the start up it gives an error.Please see:

> Log of fsck -C -R -A -a 
Sun Aug 19 20:33:33 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/hda1: Adding dirhash hint to filesystem.

/dev/hda1: clean, 11/3842720 files, 164660/7679062 blocks
fsck.ext3: No such file or directory while trying to open /dev/hda5 
/dev/hda5: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb5: 6 files, 457/1161666 clusters
open UUID=8240-F37E:No such file or directory
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb7: clean, 11/2611200 files, 126003/5217100 blocks
fsck died with exit status 9

Sun Aug 19 20:33:33 2007

And my updated fstab is:
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdb1
UUID=f4b726d6-76cf-438f-9b6a-4afdc6b15c4f / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1
/dev/hda1  /media/hda1 ext3 defaults 0 1
# /dev/hda5
/dev/hda5  /media/hda5 ext3 defaults 0 1
# /dev/hda6
UUID=8240-F37E /media/hda6 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hdb5
UUID=68E9-02F3 /media/hdb5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hdb7
UUID=d7637bbe-157f-4fc3-b8fd-3931160a45a1 /media/hdb7 ext3 defaults 0 2
# /dev/hdb6
UUID=3a5095da-41f3-4e4e-a768-0c24bf333572 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Please see the logs.

---

### Post by schorsch on 2007-08-19
It seems as if you did not create a filesystem on /dev/sda5 as you did on /dev/sda1. If you are really sure that you do not need anything on this partition create an new ext3 filesystem on /dev/hda5
```
mke2fs -j /dev/hda5
```
You could check if there is still a ntfs filesystem on it with
```
mount -t ntfs /dev/hda5 /media/hda5
```
What is the output of
```
fdisk -l
```now?

---

### Post by chatterjee on 2007-08-19
The result of the first output is:
> mke2fs 1.40-WIP (14-Nov-2006)
Could not stat /dev/hda5 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

for the second command it gives:
> mount: special device /dev/hda5 does not exist

For the third command it gives NOTHING,only opens the prompt again.:confused:
Now,what should have to be done?Any ray of hope?:(

---

### Post by schorsch on 2007-08-19
Uuuups, sorry, my fault ...
```
sudo fdisk -l
```
... it is lowercase "L" at the end!
... but it seems as if you deleted the partition /dev/hda5 when editing the partition table with gparted. So we have to know the partition scheme of your hard disk to find a solution.
Is there any running windows on your machine? I guess not as you told us you have formatted the two ntfs partitions ....

---

### Post by chatterjee on 2007-08-19
The output is:
> Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3824    30716248+  83  Linux
/dev/hda2            3825        4865     8361832+  83  Linux

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2454    19711723+  83  Linux
/dev/hdb2            2455        9728    58428405    f  W95 Ext'd (LBA)
/dev/hdb5            5100        9728    37182411    b  W95 FAT32
/dev/hdb6            2455        2501      377464+  82  Linux swap / Solaris
/dev/hdb7            2502        5099    20868403+  83  Linux

Partition table entries are not in disk order


Thanks for  your persevering effort.:D

---

### Post by amazingtaters on 2007-08-19
Make sure the UUID in the fstab is the same as the partitions actually UUID. The UUID changes when you reformat an ntfs to ext3

---

### Post by schorsch on 2007-08-19
o.k., now I understand:

You did not touch /dev/hdb so there will be no trouble with the entries in /etc/fstab.
You have deleted /dev/hda5 and dev /hda6, merged something and got a 30 GB /dev/hda1 and 8 GB /dev/hda2. In the past /dev/hda2 must have been an extended partition.
I would suggest you put an "#"  (without the quotes!) in front of every line in /etc/fstab that mentions hda5 and hda6 so that linux will ignore them when booting up. You can delete these lines later on when everything is up and running.
Have you already formatted /dev/hda2 with e.g. an ext3 filesystem? If so you should add the following line to /etc/fstab:
```
/dev/hda2   /media/hda2    ext3   defaults  0 1
``` just similar to /dev/hda1.
If not you can also add this line but again put an "#" in front of it so that linux just ignores this line at the moment and remove the '#" later when you created a filesystem on /dev/hda2. But create the directory /media/hda2 first!
If you want to you can use the UUIDs as I mentioned before but I think at the moment you are happy with /dev/hd.....

---

### Post by chatterjee on 2007-08-19
[SIZE=5][B]A [COLOR=Red]huge [/COLOR][COLOR=Blue]THANKS[/COLOR] to you all,especially [COLOR=RoyalBlue]schorsch.:D

[/COLOR][/B][COLOR=RoyalBlue][SIZE=2][COLOR=Black]After executing the fdisk -l everything seemed to be clear,we were mistaken while giving the proper drive names.

[SIZE=4][COLOR=Purple]Thanks again,it's working now.[/COLOR][/SIZE]
[/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by schorsch on 2007-08-19
Great! Glad to hear that! Could you please mark this thread as solved as it could be useful to other users, too? And as I told you, don't worry .. :-)

---

