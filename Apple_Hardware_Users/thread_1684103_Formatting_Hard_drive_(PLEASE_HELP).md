---
title: "Formatting Hard drive (PLEASE HELP)"
date: 2011-02-08
forum: Apple Hardware Users
---

### Post by xTLx on 2011-02-08
I was trying to reformat my Seagate external hard drive and I selected "free Space," in disk utility not realizing that the computer would no longer recognize the device.

I'm trying to install Snow Leopard on it so now how do I format it now to the GUID format? I luckily backed up the entire contents of the hard drive (The essential files on it), but what do I do now that the computer doesen't recognize it!? :confused:

Please help fast!... This is kind of an emergency situation.

Thanks

---

### Post by xTLx on 2011-02-08
Okay I'm trying to use Test Disk now to find the lost partition (using my PC)... I guess next when I hook it up to the Mac I should go to disk utility and use the the GUID format to reformat the hard drive?

I'm trying to install this on an external hard drive so I can boot Snow Leopard on my PC from the external hard drive... Any help?

---

### Post by srs5694 on 2011-02-08
You can start by clearly explaining things: What was the state of the drive before you started (did it use MBR or GPT, how many partitions were on it, what filesystems did they use, etc.?), what did you do (your description is so vague I can't tell), what is the current state (MBR or GPT, are there any partitions on it?), and what do you hope to do (recover some or all old partitions, use it for a fresh install, etc.?)? If there's anything on the disk now, posting the output of "sudo fdisk -lu", "sudo gparted /dev/sda print", or "sudo gdisk -l /dev/sda" would be helpful. Please post such output between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for clarity.

---

### Post by xTLx on 2011-02-08
Sorry my knowledge in this subject is pretty limited, but I CAN tell you that It's a USB connected external hard drive that originally started with one partition on it. I removed the partition and my computer no longer recognizes the hard drive so now I'm trying to create a new partition on it (because I couldn't recover the old one). I have no idea as to how I create a partition, but If I can create one I'm planning reformat it with the OSX disc utility so that I can install Snow Leopard on it. Sorry I don't really know a whole lot about formatting hard drives. Is this clear enough?

Also: I am trying to create the partition on a *PC* but I'm trying to format it with a *mac*.

---

### Post by xTLx on 2011-02-08
I guess in other words theres literally nothing on the hard drive and I want to be able to use it, but I don't know how to create a partition.

---

### Post by srs5694 on 2011-02-09
Partitions are created using any of a number of utilities, and filesystems are placed on those partitions with any of a number of utilities. Some utilities do one job but not the other, but others do both jobs.

In your case, it's best to use OS X's Disk Utility to do both the partitioning and filesystem creation. Some Googling turned up [this page,](http://macs.about.com/od/applications/ss/diskutilformat.htm) which contains a pretty basic introduction to Disk Utility. Read it and you should be fine.

One more thing: The "GUID format" you mention is a GUID Partition Table (GPT), which is a way of defining partitions. Two competing formats are the Master Boot Record (MBR) and Apple Partition Map (APM) formats. All three define disk partitions, but not the filesystems they contain. For use with a Mac, you'll probably want to use the Hierarchical Filesystem Plus (HFS+), aka the Mac OS Extended filesystem. HFS+ (like any filesystem) can be used on GPT, MBR, or APM disks. On an Intel-based Mac, GPT is the native partitioning system, and IIRC, it's required to boot Mac OS; but for an external data drive, you can use any partitioning system you like.

---

### Post by xTLx on 2011-02-09
Hey thanks man, I'll see if I can get this to work...

---

### Post by dubmartian on 2011-02-09
if you havent found it yet, its the options button under the "volume scheme" box. 
you can only select it after choosing a new volume/partition scheme but not after 
making any further changes. easy to overlook.
[IMG]http://lowendmac.com/zisman/09az/airdisk/disk-utility-partition.jpg[/IMG]

---

### Post by xTLx on 2011-02-10
Okay cool, so I have the OS installed on the hard drive now... Now the only problem is that I'm trying to boot it from my PC. I don't really know anything about hackintoshes, but I have an intel processor so I'm assuming that this should work...

I tried changing the boot priorities to boot from the external hard drive, but nothing happened. What should I do next?

---

### Post by srs5694 on 2011-02-10
You'll have to ask elsewhere about Hackintosh issues. The forum moderators frown upon such discussions here, and few people here have much experience with such configurations.

---

