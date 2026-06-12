---
title: "Xandros Uninstall"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by LE CHARBON on 2007-05-01
I have a dual boot sysytem. XP and Xandros. I want to put UBUNTU where xandros is. I have looked in the forums, but the answers are kinda vauge to me. I put the UBUNTU CD in and get to the install screen where it talks about the partitions. I am not sure which button to push after that. There several choices and numbers that I do not understand.  I do not want a triple boot. If someone could write down in some what detail as to how I remove xandros while keeping XP that would be helpful. The only reason why I keep XP is my wife likes windows, I do not. Please help in Layman's terms.

Thanks:(

---

### Post by starcraft.man on 2007-05-01
Hmmm, ok, I assume you now have XP on the first partition and Xandros on the second.

So, when you get to the partitioner in the live or alternate installer its simple. First, say you want to manually edit the partition table. Next an NTFS partition should be at the top of your list. You want to leave that alone, that should be your xp. I assume that Xandros should be listed right underneath. So if you wanna remove it just select it and delete the partition. Then you want to create 3 partitions. To create just select the free space and push enter, then you'll choose how much drive to give it. Below is how your partitioner should look, tried to make it understandable. Your Ubuntu Root parition should be primary to be booted from and you should enable the bootable flag on it. Swap and Home should be logical, their just data.

Partition List:
- XP Partition, NTFS, X GB, mount /media/hdsomething (can change)

- Ubuntu Partition, Ext3, 6-8 GB, mount /

- Swap File, Swap, 2-3 GB, doesn't mount like drives

- Home partition, Ext3, rest of your drive GB, mount /home

The / is your root directory and you mount your home seperate so that you can keep your data if you reformat your version of Ubuntu.

After your done setting it up, grub will detect your XP install unless its corrupted.

---

