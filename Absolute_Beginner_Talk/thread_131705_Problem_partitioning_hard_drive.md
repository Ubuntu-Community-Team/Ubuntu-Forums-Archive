---
title: "Problem partitioning hard drive"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by GlumJester on 2006-02-16
Right now, I have a laptop with an NTFS partition with Windows XP on it. I attempted to partition the hard drive by running Gnoppix from disk and using GParted, a suggestion from my roommate. When I attempt to resize the NTFS partition, it acts like it's doing something, then displays the partition at its original size. When I try to resize and make a new partition, it tells me that the second partition couldn't be created. I'm assuming it's because GParted doesn't resize my first partition.

I then boot Knoppix from disc and open qtparted, another suggestion from my roommate. Qtparted only shows one drive: hdc, the CD drive that Knoppix was running off of. My roommate checked and saw that the hard drive wasn't mounted. He's now stumped as to why neither method worked.

Does anyone know why I can't partition my hard drive?

Also, any other suggestions are greatly appreciated.

---

### Post by goatflyer on 2006-02-16
If you're trying to create a partition in order to install Ubuntu as dual boot, you could use the Install CD, the partitioning works and it detects and avoids your Windows partition.

---

### Post by Sutekh on 2006-02-16
Yes use the Install CD to do the partitioning.

Here is a pretty darn good guide (with screenshots) of a fairly typical install of Ubuntu with Windows (including resizing that NTFS partition)
[Installing Ubuntu + NTFS - by ]("http://users.bigpond.net.au/hermanzone/p3.htm")[Herman]("http://www.ubuntuforums.org/member.php?u=31861")

---

### Post by jamesr on 2006-02-17
If Partition Magic is anything to go by, you could not partition the booted partition, you either booted a floppy to partition the boot drive (older software ) or it drops to a RAMdisk (newer version). I don't know what the latest does. 

I also believe Qparted also operates in a similar manner.

It sounds Qtparted is operating the same way.

Install CD is good to use but first defrag the ntfs drive.

---

### Post by kennethb on 2006-02-17
When I had a dual boot Windows/Linux system. I first installed Windows and Partition Magic. I then repartitioned the hard-disk drive with Partition Magic and then installed Linux from a boot CD. However, I suggest you go with a pure Linux install. What do you need the Windows OS for?

---

### Post by don cole on 2006-02-17
My 2 cents.

I would like to point out that NTFS partition CAN NOT share files between Windows and Linux. For that you need FAT32.

There are 2 ways of doing this.

1 Starting with Windows using such to partition.
2 starting with Linux using such to partiton.

don cole

---

### Post by manicka on 2006-02-17
You may find these howtos helpful

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Luke771 on 2006-02-17
I say same thing as someone else, plus you get a walk-through for free:
To resize ntfs partitions without losing or messing up any data (well, most of the times) Partition Magic Bootable CD is the way to go. Any version from 8 up wil do.
(BitTorrent will get you that)
Remember partition magic is commercial software, you have to pay the licence before you use it. (that was kinda disclaimer, right?)
You boot from partition magic CD, resize your NTFS partition, then reboot from the  Ubuntu install CD, and when you get to built-in the partitioner choose "manually edit partition table", you will see your ntfs partition and the frree space you created with PMagic, go to the ntfs partition first, select   "mount point", and choose not to mount that partition (you can manually mount it if you need to get something frome there), or, you choose mount is as /windows if your hdd is better than bad-sector-free.
Then you install Ubuntu in the free space; when you get to the Grub install part, keep in mind that if you install Grub in the MBR you will have to us the windows install cd and the administrator password to restore a windows-only system, you can install Grub in hd0,1 (that's hd[zero][comma]1) if you have one hdd with both systems on it.
That's all, and your room mate is an a*****e ;-)

One more detail: (I'm thinking about your ntfs partition) if you mount a partition as /media/whatever you will see an icon on your desktop that accesses that partition directly; if you mount it as /whatever you will see it as a directory called whatever in your file system (I dont like mess on my desktop so I use the last option)
cya

---

### Post by plors on 2006-02-17
latest gparted (0.2.x) has drastically improved NTFS handling. maybe this can help you.

---

### Post by AndyCooll on 2006-02-17
[QUOTE=don cole]My 2 cents.

I would like to point out that NTFS partition CAN NOT share files between Windows and Linux. For that you need FAT32.

There are 2 ways of doing this.

1 Starting with Windows using such to partition.
2 starting with Linux using such to partiton.

don cole[/QUOTE]

This is not entirely true. With Linux you can _read_ files that are on NTFS partitions, you just cannot write to the NTFS partition. As mentioned above to do that on a dual-boot pc you need to create a FAT32 partition. If you have your files on a Linux server you need Samba to assist you to read and write to it.

:cool:

---

