---
title: "Because i'm an idiot. nfts-3g and mounting issues"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by pacguy on 2006-11-29
Hi guys, I've only been doing this for a week or two so I'm still trying to figure out what to do. After installing edgy I was able to read files from my windows partition and access it just fine and dandy though obviously I wasn't able to change them. Then I got to the psychocats link on mounting windows and I tried that. Nothing seemed to change except that the windows icon now listed itself as windows instead of hdc1. A while later the icon disappeared and I can't get it to come back. I tried everything I could to get it to show up again and even removed all the changes that I had made to my fstab. Then I had the bright idea to install nfts-3g thinking that it would work fine. It didn't and now I have no idea what to do.
Here's my fdisk
Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       11937    95883921    7  HPFS/NTFS
/dev/hdc2           11938       14481    20434680   83  Linux
/dev/hdc3           14482       14593      899640    5  Extended
/dev/hdc5           14482       14593      899608+  82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24321   195358401    7  HPFS/NTFS


Here's my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2
UUID=904dcd20-dc0d-455f-a1b0-9bfdf60ddd79 /               ext3    defaults,erro$
# /dev/hdc1
UUID=CCC89687C8967006 /windows     ntfs defaults,nls=utf8,umask=007,gid=46 0   $
# /dev/hdd1
UUID=6C1C20001C1FC44C /media/hdd1     ntfs    defaults,nls=utf8,umask=007,gid=4$
# /dev/hdc5
UUID=96320ba2-991d-42ab-afbf-0efe28e4d5c7 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

#/dev/hda2 /media/Windows ntfs nls=utf8,umask=0222 0 0
/dev/hdc1       /media/windows  ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
/dev/hdd1       /media/windows1 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0

Now when I try to mount /windows, /hdc1, or /media/windows using a variation of this sudo mount -t ntfs /dev/hdc1 /mnt/windows
I get this
mount: /dev/hdc1 already mounted or /mnt/windows busy

Or I try sudo mount -a and I get this fun message
mount: /dev/disk/by-uuid/CCC89687C8967006 already mounted or /windows busy
Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Failed to mount '/dev/hdc1': Device or resource busy
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Failed to mount '/dev/hdd1': Device or resource busy
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

So, like I said, I'm an idiot. If anyone could help me solve this mess I'd really appreciate it. Thanks.

---

### Post by rlozano on 2006-11-29
> # /dev/hdc1
 UUID=CCC89687C8967006 /windows ntfs defaults,nls=utf8,umask=007,gid=46 0 $
 # /dev/hdd1
 UUID=6C1C20001C1FC44C /media/hdd1 ntfs defaults,nls=utf8,umask=007,gid=4$


comment these lines if you want to mount it using ntfs-3g as shown in the last few lines of your fstab

---

### Post by pacguy on 2006-11-29
> **rlozano said:**
> comment these lines if you want to mount it using ntfs-3g as shown in the last few lines of your fstab

What type of comments do I need to leave. I have no idea what to do with that or what to write.

---

### Post by rlozano on 2006-11-29
> **pacguy said:**
> What type of comments do I need to leave. I have no idea what to do with that or what to write.

just put a # sign infront of the UUID (like this #UUID) if you want to make use of ntfs-3g in mounting.

otherwise comment out the last 2 lines of your fstab if you want to use the regular fuse ntfs in mounting your ntfs drive.

---

### Post by Adramelech on 2006-11-29
Why dont you modify yor fstab to mount the device with ntfs-3g?

I did it like this:

```
UUID=045CC12D5CC119F6 /media/hda2     ntfs-3g    defaults,locale=en_US.utf8 0 0
```

---

