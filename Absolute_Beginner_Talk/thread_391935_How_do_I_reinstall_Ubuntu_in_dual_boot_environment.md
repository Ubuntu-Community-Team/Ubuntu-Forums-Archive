---
title: "How do I reinstall Ubuntu in dual boot environment"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by wscheer on 2007-03-23
I want to reinstall ubuntu (made some changes with out making filename_bak and would like to get a fresh start) on a laptop that is dual booting windows/ubuntu.

I have a live CD running and I got to the part that deals with preparing the partitions. Not sure if I can just delete "/dev/hda2" and reinstall there without disturbing windows.

I'm pretty sure windows is the first large partion followed by ubuntu and then the boot manager.

Right now the partitions look like this.

[HTML]partion         |    filesystem     |    size       |   used     |        unused        |  flags
---------------------------------------------------------------------------------------------------------------------
/dev/hda1           ntfs                  39.19GB      34.93GB          4.26GB                boot
/dev/hda2           ext3                  15.99GB      6.42GB            9.57GB
/dev/hda3           extended           729.52MB       ---                      ---
    /dev/hda5       linux-swap        729.52MB       ---                      ---[/HTML]

Any advice on what to delete or how to overwrite would be great.

---

### Post by Hendrixski on 2007-03-23
There's a ton of documentation about this, just google ubuntu dual boot and you'll find something that can explain it way better than any of us ever could.  Because 100 heads are better than 1, and 100 heads worked together on that documentation.

Essentially don't need to repartition if you've had a previous install... the part that says NTFS, that's windows (NT is the windows kernel, and NTFS is the NT file system). you'll just go through the install and it'll ask you to pick a drive, you select the one that currently has ubuntu on it, and that's the only place that it will over-write it.

If you're a developer, and you may hose parts of your system more often, you may want to consider partitioning into hundreds of little pieces, so like one partition for root, one for /boot, another for /video, another for /whatever  depending on your needs.  But for now, you can just do one big thing and have the Ubuntu installer do allthe thinking.

---

### Post by confused57 on 2007-03-23
> **wscheer said:**
> I want to reinstall ubuntu (made some changes with out making filename_bak and would like to get a fresh start) on a laptop that is dual booting windows/ubuntu.

I have a live CD running and I got to the part that deals with preparing the partitions. Not sure if I can just delete "/dev/hda2" and reinstall there without disturbing windows.

I'm pretty sure windows is the first large partion followed by ubuntu and then the boot manager.

Right now the partitions look like this.

[HTML]partion         |    filesystem     |    size       |   used     |        unused        |  flags
---------------------------------------------------------------------------------------------------------------------
/dev/hda1           ntfs                  39.19GB      34.93GB          4.26GB                boot
/dev/hda2           ext3                  15.99GB      6.42GB            9.57GB
/dev/hda3           extended           729.52MB       ---                      ---
    /dev/hda5       linux-swap        729.52MB       ---                      ---[/HTML]

Any advice on what to delete or how to overwrite would be great.

Before you reinstall, I'd make a copy of the Super Grub Disk & the gparted live cd:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

To answer your question, during reinstallation, just select /dev/hda2 as your root(/) partition(primary partition), you don't want to save existing data, select to format ext3, then select /dev/hda5 as your swap partition(logical partition)...you'll need to do a manual partitioning...see the 1st & 2nd links in my signature, especially the 2nd for the live cd.

---

### Post by seshomaru samma on 2007-03-23
in your partition table
hda1 is windows
hda2 is linux
hda3 is the swap

if you want to reinstall , reformat hda2
its best if you create two partitions there one is / (=root) where linux will be installed and the other is /home
creating a separate home partition is a good idea , this way you can upgrade and reinstall while keeping all your data and settings
you can keep the swap as it is

---

### Post by wscheer on 2007-03-25
Just an update, I ended up reinstalling windows so I could start from scratch.
I learned a ton about partitoning that I didn't know before. It looks scary at first, but after you read a little bit about it, it's not that bad.

I followed the guide here once I had reinstalled Windows [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

Basically, the install this guy did does not use the live CD but it wasn't that hard to follow.
I came out with something like this.

20.0 GB for Windows XP Home Edition
5.0 GB for /  (root) for Ubuntu Dapper
20.0 GB for /home for Ubuntu Dapper
10.0 GB FAT32 data partition       (shared files Windows/Ubuntu)
1.0 GB Swap Area                        (memory swap)

I wish I had take some screen shots but maybe i'll sketch some figures out and repost.

I also used this conversion calculator to make sure all my partitions were nice rounded off Gigs 
[http://www.t1shopper.com/tools/calculate](http://www.t1shopper.com/tools/calculate)

Thanks again for all your help guys!

---

