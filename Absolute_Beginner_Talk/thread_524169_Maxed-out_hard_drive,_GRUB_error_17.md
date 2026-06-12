---
title: "Maxed-out hard drive, GRUB error 17"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by snowbound on 2007-08-12
Ok, here's my situation,

I have a 30gb hard drive for my laptop, a 12gb Windows partition, and a 16bg Ubuntu (plus swap space). Yesterday, I inadvertently filled up my Ubuntu partition. I was attempting to create an archive file, a particularly large one at that. I'm not sure exactly what I did, but i must have included some large extra files. Anyways, I received an error message saying that the archive had failed, and that I was out of disk space. I looked for the archive so I could delete it, but I was unable to locate it. I restarted, and afterward I could no longer log in, so I restarted in recovery mode and attempted to delete files in the /home/ directory, with no luck. I'm guessing thats where my second problem started, i must have messed something up because now when I start up I get "Error 17", which I know means it can't load the partition.  When I started up with the Live CD, and I could access my Windows partition, but I could even see or mount the other one. So, at this point I really am not sure what to do.

At least I'd like to be able to transfer some files. Even at the expense of Windows. :mrgreen:

---

### Post by oilchangeguy on 2007-08-12
here's just a quick tip, about how much swap space you don't need:

For new users, personal Ubuntu boxes, home systems, and other single-user setups, a single / partition (plus swap) is probably the easiest, simplest way to go. However, if your partition is larger than around 6GB, choose ext3 as your partition type. Ext2 partitions need periodic file system integrity checking, and this can cause delays during booting when the partition is large.

For multi-user systems or systems with lots of disk space, it's best to put /usr, /var, /tmp, and /home each on their own partitions separate from the / partition.

You might need a separate /usr/local partition if you plan to install many programs that are not part of the Ubuntu distribution. If your machine will be a mail server, you might need to make /var/mail a separate partition. Often, putting /tmp on its own partition, for instance 20 to 50MB, is a good idea. If you are setting up a server with lots of user accounts, it's generally good to have a separate, large /home partition. In general, the partitioning situation varies from computer to computer depending on its uses.

For very complex systems, you should see the Multi Disk HOWTO. This contains in-depth information, mostly of interest to ISPs and people setting up servers.

With respect to the issue of swap partition size, there are many views. One rule of thumb which works well is to use as much swap as you have system memory. It also shouldn't be smaller than 16MB, in most cases. Of course, there are exceptions to these rules. If you are trying to solve 10000 simultaneous equations on a machine with 256MB of memory, you may need a gigabyte (or more) of swap.

On 32-bit architectures (i386, m68k, 32-bit SPARC, and PowerPC), the maximum size of a swap partition is 2GB. That should be enough for nearly any installation. However, if your swap requirements are this high, you should probably try to spread the swap across different disks (also called “spindles”) and, if possible, different SCSI or IDE channels. The kernel will balance swap usage between multiple swap partitions, giving better performance.

As an example, an older home machine might have 32MB of RAM and a 1.7GB IDE drive on /dev/hda. There might be a 500MB partition for another operating system on /dev/hda1, a 32MB swap partition on /dev/hda3 and about 1.2GB on /dev/hda2) as the Linux partition.

---

### Post by snowbound on 2007-08-12
My hard drive isn't exactly 30gb, and I only have 512mb of swap space, so its about 28.5-29gb. Ntsf for my Windows partition, and ext3 for Ubuntu. I understand what you mean when you suggest breaking down several partitions, thus preventing what i got myself into (or at least deterring it). I use this computer primarily as a home computer connected to a home network, so at most I'll have 2 or 3 users on it. I suppose if worst comes to worst and I need to reformat, or the next time I set up a computer, I will use a set up like you have suggested, but at the moment I'm hoping I can still salvage whats left of my computer. Is that still possible?

---

