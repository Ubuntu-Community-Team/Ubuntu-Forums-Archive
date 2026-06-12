---
title: "linux dont detect nfts partition"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by suxxors on 2006-09-25
hmm ok.
First, i installed windows xp some time ago. I created 2 partitions: 10 gb for linux ang 50 gb for windows. I installed windows and used it for some week. now, installed ubuntu 6.06 ( i did new partition on 10 gb for swap)

the structure of my hd is:
/dev/hda1 -ext3
/dev/hda2 -swap
/dev/hda5 -windows ntfs

Hm ok. if i had installed linux, and rebooted then grub didnt recognize xp. I tried system->administration->disks to enable my nfts partition but linux was unable to do it. Then i reinstalled ubuntu. On partitioner (during install) i made my windows partition as /media/hda5 and then linux saw my windows xp files but after next restart it couldnt again.
 I have tried everything, read alot of manuals... nothing helped. Used sysresccd, nohting helped. But there has to be some way that i can restore my xp partition?

I have also used hdx,x... hdax,x in menu.lst but again nothing. ( always error 23 or 17 ...) used also rootnoverify. again nothing.

But for sure there have to be some way to get my xp partition back to restore my files. I think the mbr is 'broken'...

---

### Post by steve.horsley on 2006-09-25
Can you post the output from the command
**fdisk -l**

That should tell us what's on the disk.

---

### Post by aysiu on 2006-09-25
There are two problems here.

1. Reading the NTFS partition
2. Adding it to the Grub boot menu

For problem #1, try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

For problem #2, I'm not 100% sure this'll work, but try this: ```
sudo nano -B /boot/grub/menu.lst
``` Add in these lines at the end: ```
title           Windows XP
root            (hd0,4)
savedefault
makeactive
chainloader     +1

``` Then save (Control-X, Y, Enter).

---

### Post by suxxors on 2006-09-26
ok, the disk info is:
[I]Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1099     8827686   83  Linux
/dev/hda2            1100        1275     1413720   82  Linux swap / Solaris
/dev/hda3            1276        7295    48355650    f  W95 Ext'd (LBA)
/dev/hda4            7296        7296        8032+  83  Linux
/dev/hda5            1276        7295    48355618+   7  HPFS/NTFS[/I]


I tried both solutions aysiu gave, but again nothing: Loading xp grub says:

[I]Windows XP
root (hd0, 4)
Filesystem typre unknown, partition type 0x7
savedeafualt
makeactive
Error 12: invalid device requested[/I]

...

But maybe one solution is to reinstall xp, but it will delete grub? Ok, i tried to reinstall xp but it gave me error something like theres no space for swap file. Then i tried to delete ubuntus partition with free-dos fdisk, but it coudlnt....

---

### Post by aysiu on 2006-09-26
I've heard that sometimes Windows doesn't like being *after* Linux. Notice how the NTFS partition is the last partition in your table?

Maybe someone else can confirm this from personal experience. That's just what I've heard. Mine worked just fine with Window being on /dev/hda1. Don't do anything drastic, though, until someone more knowledgeable than I can confirm this.

---

### Post by suxxors on 2006-09-26
hmm ok thanks. But i really need help so if someone knopw something then please tell.

---

### Post by xyz on 2006-09-26
> **suxxors said:**
> hmm ok thanks. But i really need help so if someone knopw something then please tell.

Sorry but do you mean you tried what the guys suggested and it didn't work or you don't understand how to do it??;)

---

### Post by mokmoki on 2006-09-26
edit: stupid reply, didn't understand the problem fully...

---

### Post by xyz on 2006-09-26
OK! Clicking on the link aysiu gave you in above post and reading there a bit, could you specify what you don't understand..anything!
For instance...why do I have to "umount" first for my partition or even what do you mean at all. We've all at one time not understood the first thing about Linux...believe me! Don't be shy! No judges/teachers here and saying it in your words help to help you. ;)

---

