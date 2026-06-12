---
title: "Busybox deleted...Linux won't boot"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by daddydoc on 2007-01-16
I am a newbie to Linux.  With my son's help, I installed 6.10 Ubuntu server with raid.   It worked great until I deleted busybox.
1. How can I reinstall linux from the live cd to access my files?? (there were 3 partitions)
2. Or, how do I mount hds from linux cd?
3. Or, can I access infromation off of a raid hd after installing a new desktop 6.1 ubuntu linux?

Thanks in advance
1 idiot newbie linux person

Daddydoc](*,) ](*,)

---

### Post by goatflyer on 2007-01-16
If your /etc/fstab is still intact, just type

mount /dev/md0
or
sudo mount /dev/md0


If it complains about /dev/md0 not found, and you know your /etc/raidtab is still intact, just type

raidstart /dev/md0
or
sudo raidstart /dev/md0

and then the first command


If your /etc/raidtab is gone, then you'll have to remember all the decisions that were made when setting up the raid.

If any problems, but those files are still there, post them here and we'll have a look

---

### Post by daddydoc on 2007-01-19
I have totally screwed up my Linux 6.1 raid, and all I want to do is retrieve my files.  I hd is formatted and gone, the other is maybe ok

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1824    14651248+  fd  Linux raid autodetect
/dev/sdb2            1825        2067     1951897+  fd  Linux raid autodetect
/dev/sdb3            2068       48641   374105655   fd  Linux raid autodetect

(i got this info by loading the desktop ubuntu linux cd)  My linux program is not functioning right now.


the 1st partition is 15gb ext3 for the linux system
the 2nd partition is 2 gb swap partition
the 3rd partition was in xfs file format

and the 3rd partion ~375gb has my information in it that Iwant to restore.

How do I go about getting my information off the sdb raid sata drive?
thanks in advance.
daddydoc](*,)

---

### Post by daddydoc on 2007-01-19
oh the 3rd partition was in xfs file format

Daddydoc](*,)

---

### Post by goatflyer on 2007-01-21
It depends on which raid level you created.

If you created RAID level 0, there is no redundancy, and in general, when you lose 1 of the drives, you can recover nothing.  People often choose RAID0 because they like being able to add up the storage on a bunch of drives and create one big (fast) drive.  Recovery prospects are guaranteed to be zero chance if your stripe size was small.

From your description the root/boot sector was probably on the first drive and I'm guessing it was RAID 0.

If you had created the next level up (RAID1) all information would be mirrored on 2 drives.  If one failed or was accidentally formatted, then the system could be 100% recovered.  If this is what you built, then the information here will help.
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

If you only had 2 drives, it was not possible for you to have built any of the other RAID levels, so its basically down to 2.   And if it was RAID0, and you lost a drive, then I'm sorry to say your info is toast crumbs.

---

