---
title: "Transfering files from one drive to another"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by Jcrowley on 2006-06-27
Hi,I installed Ubuntu 6.06 and I really like it.Switched to it from Win2000 caused I wanted to learn about Linux.My question is:How do I go about transfering files from /home/jim to other hard drives?I'm not totally computer illiterate and have been finding a great deal of info on the forums,just a little help.Thanks ,Jim.

---

### Post by nixternal on 2006-06-27
Hey Jim,

Have you got the hard drive mounted at all?  What format is the second hard drive?  Is it ext2, ext3, reiserfs, ntfs, fat32? you can add it to fstab for automounting, or you can manually mount the hard drive. if you want, you can do a quick search in the forums for manually mounting hard drives once you have the information. good luck, and keep us informed!!!

---

### Post by Jcrowley on 2006-06-27
nixteranl,the following is what I got when I did sudo fdisk -l

jim@j2300:~$ sudo fdisk -l

Disk /dev/sda: 9110 MB, 9110016512 bytes
255 heads, 63 sectors/track, 1107 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1058     8498353+  83  Linux
/dev/sda2            1059        1107      393592+   5  Extended
/dev/sda5            1059        1107      393561   82  Linux swap / Solaris

Disk /dev/hdf: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1       14946   120053713+   c  W95 FAT32 (LBA)
jim@j2300:~$

It is showing up in Disk Manager.Also is there any way to access the drives without going into the Disk Manager?Thanks  again for your help for I'm quite willing to learn all that I can,Jim.

---

### Post by verbatim210 on 2006-06-27
all the mounted drives are located under 
/media
 -hda1
 -hda2
 -etc etc.

example (copy file from hda1 > hda2)
something@something:~$cp /home/something/filename.txt /media/hda2/

type cp --help

verbatim

---

