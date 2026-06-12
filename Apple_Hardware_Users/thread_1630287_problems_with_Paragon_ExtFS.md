---
title: "problems with Paragon ExtFS"
date: 2010-11-24
forum: Apple Hardware Users
---

### Post by c@ssie on 2010-11-24
Ok, so this is really more of an OS X question than an Ubuntu question,  but it has to do with sharing a disk with Ubuntu, so that's why I'm  asking it here.

l have a Mac, that I duel boot with MacOSX and Ubuntu. My partitions are

1: EFI 209.7 MB disk0s1 (sda1)
2: HFS+ (MacOSX) 89.1 GB disk0s2 (sda2)
3: Ext3 (Data) 880.7 GB disk0s3 (sda3)
4: Ext4 (Ubuntu) 28.0 GB disk0s4 (sda4)
5: Swap 2.0 GB disk0s5 (sda5)


I have downloaded and installed the Demo version of  [Paragon ExtFS 8.0]("http://www.paragon-software.com/home/extfs-mac/").  

When I try to copy a file to my 880 GB Data partition, while booted in  macOSX, it is extremely slow and uses 100% of my CPU. However, if I try  to copy that same file to my Data partition, when booted into Ubuntu, It  is fast and uses very little CPU. At first, my Data partitions was  Ext4, and had the same problem. I reformatted it to Ext3 to try to solve  it. 

I don't have the same problem, when copying a file to my 28 GB Ubuntu partition.

---

### Post by lael on 2010-11-25
Yea, Paragon's ExtFS is slowww with my ext4 parition too.  Yes you *can* see your parition but it is really really slow - especially when having multiple finder windows open to the same directory.

---

