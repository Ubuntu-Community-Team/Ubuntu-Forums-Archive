---
title: "Hdd"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by evansa4 on 2005-08-22
Hi guys i have install ubunt linuxs and when i was on xp i had 2 hdd but on linuxs it only picking up one any idears

i have install linuxs on my 10 gig and have a 20 gig speare were has it gone

---

### Post by skoal on 2005-08-22
Your 20 gig'er is still there, but it's just very shy and probably a little embarassed since you moved from XP to Linux.  For some drives, it takes a while for them to come out of their shell after such a dramatic change.  Give it about a week or so and you'll probably see it again in the filemanger...

If you don't want to wait for your second drive to get over it's embarassment, you can do this:

1. open up a terminal and type:
> cd ~
sudo mount -t ntfs -o ro,auto,uid=1000,gid=1000 /dev/hdb1 /mnt
You can replace "auto" above with either "vfat" or "ntfs" if you know how you formatted that slave drive (hdb) in Windows.  XP uses "ntfs" by default and older version of WinX used "vfat" (fat16/32).

2. then change to the /mnt directory and it will be there:
> cd /mnt && ls
All your old files should show up now.  That's just a temporary fix however.  To make it permanent so that the drive will always show up each time you boot, you will need to make a few changes.  Read this wiki [entry ](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29) on how to do that.

* In that guide, however, you will replace _all_ instances of "hda" with "hdb" (hda -> hdb, hda1 -> hdb1, etc.)

cleanup temporary step before making it permanent:
> cd ~ && sudo umount /mnt
make it permanent (for each reboot):
> sudo mkdir -p /mnt/winXP
I'll _assume_ you originally used that second drive as one big "ntfs" partition in WinXP.  If not, read that wiki entry and follow the part about using "fdisk -l".  Edit the fstab file using gedit:
> sudo gedit /etc/fstab
Add the following line to the end of the file..
> /dev/hdb1                    /mnt/winXP              ntfs            ro,auto,uid=1000,gid=1000 0 0
Save the file, and:
> sudo mount -a
which will remount all drives in the fstab file.  You should be able to see that drive now by using a file manager (looking under /mnt/winXP) or simply change to that directory and 'ls' it...

Now, every time you use a file manager (or even a terminal), your old WinXP second hard drive data will show up under the directory '/mnt/winXP'.

\\//_

/edit fixed 'hdb' typo.  It now reads 'hdb1' as it should.

/edit changed a few instructions. They pertain to his unique setup only, since he has one partition which is "ntfs".

---

### Post by evansa4 on 2005-08-22
ok tryed the fist command and this came up

adam@Adam:~$  sudo mount -t auto /dev/hdb /mnt
mount: /dev/hdb already mounted or /mnt busy

---

### Post by xmastree on 2005-08-22
[QUOTE=evansa4]i have install linuxs on my 10 gig and have a 20 gig speare were has it gone[/QUOTE]Do you have two actual hard disks? Or two partitions on one disk.
[**This**](http://www.ubuntuguide.org/#mountunmountntfs) will help you to mount the windows disk. It it's ntfs you won'd be able to write to it, only read.

---

### Post by skoal on 2005-08-22
Post back what "cat /proc/partitions" says...

oops! By the way, that should be "hdb1", not "hdb" in that mount command I gave at the start.  I made an assumption that it was one big partition.

\\//_

---

### Post by evansa4 on 2005-08-22
that command says 

adam@Adam:~$ cat /proc/partitions
major minor  #blocks  name

   3     0    9770544 hda
   3     1    9333733 hda1
   3     2          1 hda2
   3     5     433723 hda5
   3    64   20005650 hdb
   3    65   19992861 hdb1
 254     0    9333733 dm-0
 254     1     433723 dm-1
 254     2   19992861 dm-2

---

### Post by skoal on 2005-08-22
Yeah, it's a physical second drive (and not another partition off your first).  You should be able to follow what I posted above in combination with that wiki link I provided as well.  I fixed the 'hdb' typo to read 'hdb1' (since your entire disk is one huge partition like I originally assumed).  hda or hdb just refers to the entire disk, not any specific partition.

What part are you stuck on?

\\//_

---

### Post by evansa4 on 2005-08-22
can u help me step by step please


what do i do first

---

### Post by skoal on 2005-08-22
Send me a private message and I'll give you my AIM account.  I got the next hour to burn and I'll step you through the process (if you can't follow the above guidelines).

\\//_

---

### Post by evansa4 on 2005-08-22
ok pmed u and cheers in advaced

---

