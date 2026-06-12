---
title: "Splitting filesystem across 2 drives"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by mundofine on 2006-06-18
I have two IDE hard drives. The master and boot drive is 6GB; the slave is 80GB. I am not dual-booting.

I installed Dapper Drake on the 6GB, but also allowed the installer to partition and format the 80GB as ext3. Installation went fine and I have no problems with the OS. On either drive, the installer created a swap partition, and then one big partition of empty space (which is where / is on the 6GB).

However, the 80GB drive is not mounted. I've done some reading and I think I can resolve that. My real question is how do I 'move' folders like /home, /opt,  /usr,  /var and /tmp onto the 80GB drive, versus the 6GB?

I'd like to have these directories on the 'big' drive before I start installing a lot of software, but I don't want to hose/re-install the OS. Surely it's not as simple as dragging-and-dropping the folders in Konqueror, right?

I've read a fair bit about the filesystem and mount points, but can't seem to find this particular topic--apologies if it's something obvious.

Sincere thanks for any help.

---

### Post by jgoguen on 2006-06-18
0.  Back up your data elsewhere (not in the original folder) and unmount the partition if it's mounted.
1.  Edit /etc/fstab so the new mount point is on the big drive (or create it if one didn't already exist).
2.  Mount the partition, change permissions as necessary, and move the backed up data into the folder.

There may be KDE tools to do some of this for you, but I'm not familiar enough with KDE to say what's there and what isn't.  I've done this a few times, most recently to move my home folder onto a new SATA drive I picked up a couple months ago.

---

### Post by aysiu on 2006-06-18
I can tell you how to move home: [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by catlett on 2006-06-18
I hate to say it but...you should really reinstall.

Get gparted live. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) It is a partitioner that runs off a live cd. It is a small download, only 30mb. Make your partitions ahead of time. I would only put boot, swap and / (/ as you know is the symbol for root) on the 6gb. That is plenty of space. Boot should be at the head of the first drive, swap and root should be next to each other. Boot only needs 50 to 100mbs. It will hold grub abd your kernels, Swap is twice your ram but you'll never need more than 1gb. That will leave root with 5+gb which is 2  more than it really needs.
The other drive should be divided up into usr, var, tmp and home. Home should be the biggest. Followed by usr,tmp and var. I follow this section 
> Everything in your linux file system can go in the same (single) partition. However, there are circumstances when you may want to restrict the growth of certain file systems. For example, if your mail spool was in the same partition as your root fs and it filled the remaining space in the partition, your computer would basically hang.

/var - This fs contains spool directories such as those for mail and printing. In addition, it contains the error log directory. If your machine is a server and develops a chronic error, those msgs can fill the partition. Server computers ought to have /var in a different partition than /.

/usr - This is where most executable binaries go. In addition, the kernel source tree goes here, and much documentation.

/tmp - Some programs write temporary data files here. Usually, they are quite small. However, if you run computationally intensive jobs, like science or engineering applications, hundreds of megabytes could be required for brief periods of time. In this case, keep /tmp in a different partition than /.

/home - This is where users home directories go. If you do not impose quotas on your users, this ought to be in its own partition.

/boot - This is where your kernel images go. See discussion above for placement on old systems. Which is part of this larger html guide on partitions [http://www.tldp.org/HOWTO/Partition/](http://www.tldp.org/HOWTO/Partition/)

---

### Post by aysiu on 2006-06-18
If I were you, I'd use PartImage to copy your existing installation to the 80 GB hard drive, and just use that 80 GB as your main thing.

[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

The 6 GB drive is neglible, and it can just be added as an additional data partition--or maybe your separate /home partition (you'd probably have to put your data somewhere else and maybe symlink it to be "inside" of /home)

---

### Post by mundofine on 2006-06-19
Thank you so much to all who replied. Those were the kind of detailed pointers I needed. I'm impressed already with the forum and the great folks providing answers. Again, thank you all for your time and the help--you guys are great!

---

