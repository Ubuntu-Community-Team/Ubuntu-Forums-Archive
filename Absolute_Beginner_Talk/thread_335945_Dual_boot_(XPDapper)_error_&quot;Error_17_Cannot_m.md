---
title: "Dual boot (XP/Dapper) error &quot;Error 17: Cannot mount selected partition&quot;"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by flexible on 2007-01-11
Dear forum,

I recently installed Ubuntu Dapper Drake (Linux kernel 2.6.15-26-386) using Live CD as a Dual Boot with windows XP. 

Hard Drives are: 

hda1 (NTFS, Win XP boot)
hda5 (FAT)
hda6 (FAT)
hda7 (Linux Swap)
hda8(Linux Ext 3)


After installation, as i felt size of my new Ubuntu swap was very low (2GB), using 'norton partition magic' in win XP, i made some changes to the windows drive hda6. What i did was, made a new partition and formatting it in linux swap. I used partition magic, because i thought if i partition my windows (FAT) hard drives using GParted (GNU Partition Editor), all data will be lost.

Now,i tried to log into Ubuntu in GRUB. The following error message appears:



> [FONT="Courier New"]booting 'ubuntu, kernel 2.6.15-26-386/root (hd0,7)

Filesystem type unknown, partition type 0x82

kernel /boot/umlinuz-2.6.15-26-386 root=/dev/hda8 ro quet splash

Error 17: cannot mount selected partition

press any key to continue..[/FONT].


when i press any key, it take me back to GRUB.
I also tried to log-in to the ubuntu recovery consol, but same error happens. I could login to XP,no problems.

Could anyone kind enough to advise me what to do? I am very new to linux.

Cheers

---

### Post by riven0 on 2007-01-11
Ouch! You used partition magic to resize a partition with Linux already on the drive? *sigh* Last time I attempted such a thing it wiped out Ubuntu for me... :-| 

Anyway, first make sure your partition no's didn't change. If so, you'll have to update the Grub menu. If not........ I'll leave it to someone else to give a better suggestion.

---

### Post by Sef on 2007-01-11
To install Linux you need to use ext 3.   Linux will not boot off of NTFS or FAT32.

Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing") (for a Live CD install.)

Read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") (for an alternate install.)


Don't use partition magic.  PM and Linux don't get along well.   Instead either use the partitioner on the install disk or get [GParted]("http://gparted.sourceforge.net").

---

### Post by confused57 on 2007-01-11
> **flexible said:**
> D\

Could anyone kind enough to advise me what to do? I am very new to linux.

Cheers

Try booting up with the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".

This will show your partitions on your disk, post the results(copy&paste), & hopefully someone here will be able to help

By the way, the gparted live cd(30 mb download) is an excellent partition tool:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

