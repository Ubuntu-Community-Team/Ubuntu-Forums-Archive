---
title: "Partitioning - quickie howto"
date: 2006-12-21
forum: Apple PPC Users
---

### Post by stream303 on 2006-12-21
I thought I'd toss in a quickie howto for anyone wanting to do manual partitioning.  It isn't really comprehensive, but just an example of how I did it with a bare drive that doesn't already contain the Apple and New World partitions.  Normally I just tell it to use the whole drive and figure out all 4 partitions for me, but I have also done it manually.

We'll assume you want to dedicate the whole drive to Ubuntu - with 4 partitions for simplicity:

1) Apple partition
2) New World partition
3) ext3 partition for Ubuntu
4) swap

When I used manual partitioning in the text-based installer, I used this configuration

**1)**  31.5 **K**
Name: Apple
Use as: do not use
bootable flag off

**2)** 977 **K**
Name: untitled
Use as: NewWorld boot partition
**bootable flag on**

At this stage, I just wrote the partition table to the disk and let the installer complain.  I then went *back* and used *guided partitioning* to install to **free space**.  It automatically set up partitions 3 and 4 for me.

Yes, you could partition 3 and 4 yourself (choosing the sizes yourself), and this is what guided partitioning came up with for my little 40gb drive:

**3)**  35.39 Gb (majority of drive space)
Name: untitled
Use as: ext3 journaling file system
Mount point:     /
Mount options:  defaults
Label:     none
Reserved Blocks:   5%
Typical Usage:    standard
Bootable flag:   off

**4)** 1.87G  (little more than twice my ram)
Name:  swap
Use as:  swap area
Bootable flag:  off

I then instructed the installer to write all these partitions to disk even though 1 and 2 had already been written.  Bingo!  Telling the partitioner to use the whole drive is the easiest, but in case you have to do it  manually, here it is...

Hopefully this helps someone get started!

---

