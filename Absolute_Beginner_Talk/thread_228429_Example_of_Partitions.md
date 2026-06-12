---
title: "Example of Partitions"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by zisme on 2006-08-03
Could someone give me a good example (preferably a screenshot of gparted if possible) of how to set up partitions so that I have all the Linux ones, and have a fair amount of shared space? I have a 120 GB hard drive and 512 MB of RAM. Thanks!

PS: I'd also like to know if they should be Logical, extended, or whatever.

---

### Post by wieman01 on 2006-08-03
I am assuming that you don't have dual boot. So here is my recommendation:

/[root] >> ext3, primary partition, 10GB
/home >> ext3, logical partition, 5GB
/[swap] >> 1GB (2 x size of RAM)
/data >> ext3 or FAT32; logical partition; 104GB

Use Windows' PartitionMagic to partition your HD. That's the easiest way to go I reckon. FAT32 for the data partition if you need to share your data/files with Windows machines.

Sadly I cannot provide you with a screenshot.

---

### Post by zisme on 2006-08-03
Actually, I am doing a dual boot. I guess I didn't mention it. I have an idea of where to cut it out. Isn't there a program so you can use Windows with Ext 3? I think it's like FS-Drive or something. Thanks again!

Zisme
PS: Would it be okay to use GParted?

---

### Post by zisme on 2006-08-03
Also, is it better to do partitioning bit by bit or all at once? Or does it matter?

---

### Post by RRS on 2006-08-03
Use gparted. Partition Magic is reported to have/create problems with Linux.

You can partition your drive in advance with the live cd or gparted is available as a standalone live cd [here]("http://gparted.sourceforge.net/livecd.php").

If you're using the alternate install cd then creating your partition tables manually during the installation works well but with the live cd doing it beforehand is better.

[This guide]("http://psychocats.net/ubuntu/installing.html") is for the live, [this one ]("http://users.bigpond.net.au/hermanzone/index.htm")for the alternate.

The safest way to share a data partition between windows and Ubuntu still seems to be with a Fat32 partition though a couple new options are in the "how to's" of the forums.

As always, before installation backup any valuable data from windows and defrag.

---

