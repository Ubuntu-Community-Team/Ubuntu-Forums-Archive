---
title: "Enough Room to Dual Boot"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by WayOutWest on 2007-05-28
I want to dual boot my windows xp sp2 laptop with Kubuntu. I defragged and compressed multiple times. I defragged 5 times and this is all I got. is this enough to repartition and dual boot?

[IMG]http://farm1.static.flickr.com/193/517835693_eb9d561ebf.jpg?v=0[/IMG]

---

### Post by Acglaphotis on 2007-05-28
28 gigs is enough to dual boot, but remember always backup first before trying to dual boot and read [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing") for more info.
-Acgla

---

### Post by starcraft.man on 2007-05-28
28 GB is more than enough, the *ubuntu install is small. You only really need two partitions, Root (/) should be minimum of 6 GB (allows room for installing lots of apps) and your swap file (like paging file in windows) should be twice your ram (thats the rule of thumb I use, up to 2 GB at the most, you don't usually need more than that).

So you have plenty of space, you only really need 8 GB for an Ubuntu install. Oh and here is a good guide to [live CD]("http://www.psychocats.net/ubuntu/installing") install. Theres also an alternate install guide if your using that. Do back up anything critical, and have fun :)

---

### Post by oilchangeguy on 2007-05-28
> **WayOutWest said:**
> I want to dual boot my windows xp sp2 laptop with Kubuntu. I defragged and compressed multiple times. I defragged 5 times and this is all I got. is this enough to repartition and dual boot?

[IMG]http://farm1.static.flickr.com/193/517835693_eb9d561ebf.jpg?v=0[/IMG]

i'd suggest a second hard drive. if your computer has the room. the one you have is getting tight on space, and the last thing you want to do is crowd either operating system. but if you want to use your present drive, it can be done.

---

### Post by dptxp on 2007-05-28
Give 6 GB to /, 2 GB to SWAP and format rest (FAT32 or ext3) for data. In case of ext3 you need a small program in windows to r/w.

Since you may not r/w NTFS properly from Ubuntu, best is to take out unwanted data, backup rest data, reduce the Windows partition to minimum first. Then make your /, Data and SWAP partitions, I prefer SWAP at the end.

Just do not format data partition in NTFS, Ubuntu Live CD anyway may not have the option.

Yes, you got enough room.

---

### Post by oilchangeguy on 2007-05-28
you don't need a 2gb swap file. that's a complete waste of space. no more than 512mb. just as in windows, if your computer needs to use swap/virtual memory, then you've got a computer with problems.

---

### Post by dptxp on 2007-05-28
> **oilchangeguy said:**
> you don't need a 2gb swap file. that's a complete waste of space. no more than 512mb. just as in windows, if your computer needs to use swap/virtual memory, then you've got a computer with problems.

Maybe, but unless I have a real tiny HDD, less than 20 GB, I prefer to be liberal with SWAP.
I may be wrong. But increasing SWAP later may be a real problem.

---

### Post by oilchangeguy on 2007-05-28
> **dptxp said:**
> Maybe, but unless I have a real tiny HDD, less than 20 GB, I prefer to be liberal with SWAP.
I may be wrong. But increasing SWAP later may be a real problem.

go to system, admin, system monitor. and look at how much swap your computer is NOT using. please post back with your results.

---

### Post by WayOutWest on 2007-05-28
in kubuntu's parition porgram, when trying to change the partition, I get an error message saying I cannot complete the process. suggestions?

---

### Post by Happy_Man on 2007-05-28
> **oilchangeguy said:**
> you don't need a 2gb swap file. that's a complete waste of space. no more than 512mb. just as in windows, if your computer needs to use swap/virtual memory, then you've got a computer with problems.

Oy! Are you saying my computer has problems? :razz:

@ OP: Does it give anything more specific than that?

---

### Post by WayOutWest on 2007-05-28
I tried using QTparted and it said that "NTFS not supported"

---

### Post by Happy_Man on 2007-05-28
I thought Kubuntu used GParted.... *goes off to check*

---

### Post by WayOutWest on 2007-05-28
nope, QTParted. it just won't make any changes to my HD in any prog. suggestions?

---

### Post by Happy_Man on 2007-05-28
Odd.... QTParted never gave me problems installing Kubuntu.....

Try opening up Konsole from the LiveCD (System --> Konsole in K menu) and typing:
```
sudo apt-get install ntfsresize
```

That's listed as a dependency on the homepage of QTparted, perhaps it will work.

---

### Post by abn91c on 2007-05-28
you have enough free space, to save yourself a headache download Wubi(windows ubuntu installer) from here:  [http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)
It will install ubuntu 7.04 like a windows program and allow dualboot. Setup is painless and automatic for the most part. Just follow the easy onscreen prompts and it will do everything for you including the partitioning(needs only about 6 gig of space, mine it took a total of 3.5) Now I dual boot with a Dell dimension 2400 windows XP and ubuntu.

---

### Post by WayOutWest on 2007-05-28
thanks for the suggestion, but does it work as well as making a separate partition?

---

### Post by abn91c on 2007-05-28
wubi will make the partition during setup automatically

---

### Post by dptxp on 2007-05-29
> **oilchangeguy said:**
> go to system, admin, system monitor. and look at how much swap your computer is NOT using. please post back with your results.

It does not use much, I have seen about 100 MB last time,  but I have not tried to check while editing multiple images. I had problem in Windows with low virtual memory and had to increase for some similar work. I think that more SWAP shall be needed if I run many applications at same time. It is just to be on safe side.

If you have some proper explanation on this, I shall be happy to learn.

---

### Post by oilchangeguy on 2007-05-29
> **dptxp said:**
> It does not use much, I have seen about 100 MB last time,  but I have not tried to check while editing multiple images. I had problem in Windows with low virtual memory and had to increase for some similar work. I think that more SWAP shall be needed if I run many applications at same time. It is just to be on safe side.

If you have some proper explanation on this, I shall be happy to learn.

found this, to help you learn:
A.3. Recommended Partitioning Scheme
Prev  	Appendix A. Partitioning for Ubuntu 	 Next
A.3. Recommended Partitioning Scheme

For new users, personal Ubuntu boxes, home systems, and other single-user setups, a single / partition (plus swap) is probably the easiest, simplest way to go. However, if your partition is larger than around 6GB, choose ext3 as your partition type. Ext2 partitions need periodic file system integrity checking, and this can cause delays during booting when the partition is large.

For multi-user systems or systems with lots of disk space, it's best to put /usr, /var, /tmp, and /home each on their own partitions separate from the / partition.

You might need a separate /usr/local partition if you plan to install many programs that are not part of the Ubuntu distribution. If your machine will be a mail server, you might need to make /var/mail a separate partition. Often, putting /tmp on its own partition, for instance 20 to 50MB, is a good idea. If you are setting up a server with lots of user accounts, it's generally good to have a separate, large /home partition. In general, the partitioning situation varies from computer to computer depending on its uses.

For very complex systems, you should see the Multi Disk HOWTO. This contains in-depth information, mostly of interest to ISPs and people setting up servers.

**With respect to the issue of swap partition size, there are many views. One rule of thumb which works well is to use as much swap as you have system memory. It also shouldn't be smaller than 16MB, in most cases. Of course, there are exceptions to these rules. If you are trying to solve 10000 simultaneous equations on a machine with 256MB of memory, you may need a gigabyte (or more) of swap.**

On 32-bit architectures (i386, m68k, 32-bit SPARC, and PowerPC), the maximum size of a swap partition is 2GB. That should be enough for nearly any installation. However, if your swap requirements are this high, you should probably try to spread the swap across different disks (also called &#8220;spindles&#8221;) and, if possible, different SCSI or IDE channels. The kernel will balance swap usage between multiple swap partitions, giving better performance.

As an example, an older home machine might have 32MB of RAM and a 1.7GB IDE drive on /dev/hda. There might be a 500MB partition for another operating system on /dev/hda1, a 32MB swap partition on /dev/hda3 and about 1.2GB on /dev/hda2) as the Linux partition.

For an idea of the space taken by tasks you might be interested in adding after your system installation is complete, check Section C.2, &#8220;Disk Space Needed&#8221;.
Prev  	Up 	 Next
A.2. The Directory Tree  	Home 	 A.4. Device Names in Linux

---

### Post by dptxp on 2007-05-30
Thanks, this thread shall be used as reference.

There is one point I am yet to understand, making SWAP proportional to RAM, some say same as RAM, some say 2 times RAM. Since SWAP is used as RAM (I think so ), SWAP should be more if RAM is less so that total is high.

And how do I see memory usage in Windows XP. I am surprised to see Low Memory notice with 4 GB of virtual memory in XP.

---

### Post by gn2 on 2007-05-30
I hope you're not forgetting to factor in the unused space that NTFS requires for proper operation and defragmenting. 12% absolute minimum, and 30% recommended.

Which means that you could be doing with more hard drive space already.

This link is for W2k, but same rules apply for all NTFS systems.
[http://www.microsoft.com/technet/prodtechnol/windows2000serv/maintain/optimize/w2kexec.mspx](http://www.microsoft.com/technet/prodtechnol/windows2000serv/maintain/optimize/w2kexec.mspx)

---

