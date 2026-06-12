---
title: "Partition question"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by bogey on 2006-03-30
I currently have 2 hard drives and am running Windows XP, both drives have been formatted NTFS.  I plan on installing Ubuntu on the 2nd hard drive; it is 160GB and I just use it for storage space, so I have plenty of space available.

I have been reading the Ubuntu + NTFS Dual Boot article and this forum and want to confirm the partition set-up.

The article says to create a fat 32 partition; will this partition be for my home directory?  If yes, is there anything that I need to do to make it my home directory or will Ubuntu do it automatically.

Another forum email said it would be a good idea to create an additional partition for future Ubuntu upgrades (e.g., Dapper, etc.).  So I should end up with the following:
- 10GB ext3 bootable partition for root
- 10GB fat 32 partition for home
- 2GB partition for swap (I have 1GB of RAM)
- 10GB ext3 bootable partition for future upgrade
- Remaining will stay NTFS for Windows

Is this a good setup or does anyone have a better recommendation?

---

### Post by SkimWear on 2006-03-30
i'd say just make a 20gb ext2 partition and the 2gb partition for swap. 10gb ex2 (dont necessarily have to have an "upgrades" partition, but it may be wise) remaining can stay NTFS if youd like.

ext2 is what i formatted my drive to and I believe (correct me if i'm wrong) you can read/write from linux/windows on this type of format.

i'd say give more space to linux :) after using ubuntu for a while you'll start taking away from windows and giving more to ubuntu.

---

### Post by Princey on 2006-03-30
I'm not sure where you got that info, but I strongly disagree (I'm sure others will too) using FAT32 for your /home directory. FAT32 doesn't not carry file permission errors and that can spell danger in case of accidental tinkering. I'd advise you to go with the default ext3. As for partioning, you can do it while installing Ubuntu. Here's a link to a great how to setup dual booting and partitioning: [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

The use of a FAT32 partition is only if you want to share stuff with your Windows partition say your music although if you search around you can find tools that read ext3 partitions under Windows. I'm not sure as to the general opinion on that aspect so I rather not say much about it. However, please not that you'll have to mount the Windows Partition if you want to see it. Also, Linux can see NTFS partitions so if you have stuff on there you can access it once you've mounted the drives.

---

### Post by alter_ego on 2006-03-30
[QUOTE=bogey]- 2GB partition for swap (I have 1GB of RAM)
[/QUOTE]

Swap is in HDD, dont worry abt it too much, i had managed to install Ubuntu with 250 MB of swap partition.

FAT32 partition is used as a common area to share data between windows and Ubuntu.

All the best!

---

