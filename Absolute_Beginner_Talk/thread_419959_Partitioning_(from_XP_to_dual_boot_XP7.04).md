---
title: "Partitioning (from XP to dual boot XP/7.04)"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Emerpus on 2007-04-23
I've decided to give 7.04 a try on my main machine and could use a little advice on partitioning during install.

This is how my partition table looks currently:

**// Partition 1 (2 GB) // Partition 2 (50 GB) // Free space (unformatted 414 GB) **

Partition 1= NTFS (C: used for Windows XP pagefile)
Partition 2= NTFS (E: used for Windows XP)

This is what I plan on:

**// Partition 1 (2 GB) // Partition 2 (50 GB) // Partition 3 // Partition 4 // Partition 5 // Partition 6**

Partition 1= NTFS 2,0 GB (C: used for Windows pagefile)
Partition 2= NTFS 50,0 GB (E: used for Windows XP)
Partition 3= FAT32 (used for shared storage)
Partition 4= Ubuntu /home
Partition 5= Ubuntu 7.04 main partition
Partition 6= Ubuntu swap

Since I don't want to risk messing anything up I would really appreciate it if someone would walk me though the process. I'm sure it's not very difficult but as mentioned I prefer to be on the safe side rather than to experiment on my own in this case.

Also, how much disk space would you allocate for the Ubuntu related partitions (main Ubuntu partition, /home partition and swap partition respectively)? As you can see I have plenty of disk space but of course there is no point in wasting it on too large partitions for e.g. swap and /home partitions. My machine has 2 GB of ram in case this has anything to say in relation to the recommended size of the swap partition. Btw. I know that a separate partition for /home is not absolutely necessary but I've read that is might be handy especially when upgrading Ubuntu in the future. Is this also something you can confirm?

---

### Post by Cypher on 2007-04-23
Ubuntu can easily access NTFS partitions, so you don't need to make a FAT32 partition, but that's entirely up to you.

For Ubuntu, if you're going to use 3 partitions, you can make the SWAP == RAM. The main partition is where the OS and all applications are going to go, so you want to make sure you give yourself enough space here. So something like 50GB would be perfectly fine. And if you intend not to use whatever is left over for Windows, then you can devote all of that to /home.

Regards

---

### Post by vree13 on 2007-04-23
I found this page to be quite helpful in partitioning, especially when dual booting:
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by az on 2007-04-23
> **Emerpus said:**
> 
Since I don't want to risk messing anything up I would really appreciate it if someone would walk me though the process. I'm sure it's not very difficult but as mentioned I prefer to be on the safe side rather than to experiment on my own in this case.

...I know that a separate partition for /home is not absolutely necessary but I've read that is might be handy especially when upgrading Ubuntu in the future. Is this also something you can confirm?

I would suggest just taking the default and letting the installer do the partitioning.  It is simple and safe - you won't make any mistakes.

You can use this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
to make your linux filesystem appear as a native windows filesystem.  No need to make a seperate partition to share.

As for a home, no, you don't need to have a seperate home to easily upgrade.  If you mess up your system, you can re-install, but preserve the home partition.  I just find it easier and simpler to just back things up the old fashined way.  As well, configurations are stored in your home drive.  If you bork up your panel and can't figure out how to fix it for example, re-installing and re-using your home partition will just keep the problem there.  YMMV.  

You don't want to cause yourself headaches by making any partition too small - if you run out of space with a full partition, you are not able to adjust the sizes of your partition anymore since they are full - again, a lot easier to just leave everything on one partition.

By default, the Ubuntu installer puts everything on one partition.  Your swap partition is also created by the installer and it is anywhere between 1.5 and 2 times your ram, depending on how much space you have.

---

### Post by Emerpus on 2007-04-23
Thanks guys, you :guitar: 

I will go with the default installation and fewer partitions then. Especially the tip from az about Ext2 IFS convinced me. :)

---

