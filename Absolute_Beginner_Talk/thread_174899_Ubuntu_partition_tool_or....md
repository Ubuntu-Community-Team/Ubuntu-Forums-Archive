---
title: "Ubuntu partition tool or...?"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-05-12
Hello all,

I am preparing to install and just wanted some input on the partitioning. I have partitionmagic 8, but was curious about several things.

1. Should I pre-partion the drive using PartitionMagic and what file sytem type should I use.  I have NTFS now.  It gives several options--FAT, NTFS, Linux ext 1 + 2 or swap, I am pretty sure I am not going to use the latter. 
2. should I use the partition tool on the Ubuntu CD?

The manual I am reading is not exactly clear on this.

Thanks in advance,

KK

---

### Post by mostwanted on 2006-05-12
[QUOTE=KarmaKing]Hello all,

I am preparing to install and just wanted some input on the partitioning. I have partitionmagic 8, but was curious about several things.

1. Should I pre-partion the drive using PartitionMagic and what file sytem type should I use.  I have NTFS now.  It gives several options--FAT, NTFS, Linux ext 1 + 2 or swap, I am pretty sure I am not going to use the latter. 
2. should I use the partition tool on the Ubuntu CD?

The manual I am reading is not exactly clear on this.

Thanks in advance,

KK[/QUOTE]


Do you need to resize anything? Then use Partition Magic and leave free space for Ubuntu.

Everything else you should do from the Ubuntu installer.

---

### Post by Kobalt on 2006-05-12
The best thing to do, I think, is to defragment your disk, backup all your files then start a Live CD session of Ubuntu and partition your disk with Gparted.

---

### Post by Mike_N on 2006-05-12
The partitioning tool that the Ubuntu installer uses has always worked great for me. Otherwise, i like G-Parted a lot more then Partion Magic. It's free for one and i've had much better results with it. It comes it two forms, a boot disc or a program to be used within an OS. Try out the boot disc... MIke

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by KillrBuckeye on 2006-05-12
[QUOTE=Kobalt]The best thing to do, I think, is to defragment your disk, backup all your files then start a Live CD session of Ubuntu and partition your disk with Gparted.[/QUOTE]Based on my horrible experience, I'd advise against this method *if* you plan to make NTFS partitions.  When I created NTFS and FAT32 partitions using GParted on the Ubuntu LiveCD, they were not mountable in Windows!  Windows could see them and recognized the filesystem, but would not assign a drive letter or reformat them.  I have since learned that the version of GParted on the LiveCD is very old and has some problems supporting NTFS partitions.  It worked perfectly for my Linux partitions, but completely botched the NTFS and FAT32 partitions that I created.  The partition table was so screwed up that when I tried to delete the NTFS and FAT32 partitions, it took my Linux /home and swap space partitions with it...  Details are described in this thread:

[http://www.ubuntuforums.org/showthread.php?t=172756]("http://www.ubuntuforums.org/showthread.php?t=172756")

Anyhow, I'd suggest using a GParted LiveCD instead which should be using the latest version.  I've been told that this version has no problems supporting NTFS.

What I ended up doing was creating the NTFS and FAT32 partitions using Windows Disk Management, and GParted for the all the Linux partitions.  This seemed to work without problems.

---

### Post by DA_uf on 2006-05-12
I'd recommend the System Rescue CD with its QtParted and Partimage.  See my Recovery Best Practices thread [http://www.ubuntuforums.org/showthread.php?t=173550](http://www.ubuntuforums.org/showthread.php?t=173550)

But you may need to read closely about any NTFS issues.

I've been satisfied with Ubuntu's partitioning to install the system.  But since I need a recovery procedure, I have made a backup partition on the same drive using QtParted.  As an alternative, you can backup to a remote drive and compress the image as well.

---

