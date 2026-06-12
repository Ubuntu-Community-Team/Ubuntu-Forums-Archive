---
title: "Does Ubuntu create its own Partiton?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by NonStop on 2007-08-15
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Basically, I will have Vista in one partition, pre-installed, and I would like to create another partition for Ubuntu. Does Ubuntu already do this? 

After creating these two partitions, I would like to create another partition for my files, but that isn't top priority at the moment.

---

### Post by Steve1961 on 2007-08-15
Ubuntu will offer to resize your vista partition if it needs space and then create the partitions it needs for installation.  However, I would use either the gparted live cd or a windows partitioning programme to create the space first, then create a data partition - fat32 would allow windows and linux to read and write to it.  I'd then install Ubuntu and let it install to the free space - it will automatically create the partitions it needs there.

---

### Post by Inxsible on 2007-08-15
Yes, Ubuntu can create a partition itself if you select the correct options. A better bet is to create your partitions manually and then start the install. Make sure you defrag your windows a few times.

IMHO, i would rather create partitions manually and know for sure what partition is being used for what, rather than have them auto-created.

---

### Post by NonStop on 2007-08-15
Ok, and I can use the Disk Management in Windows Vista to create my own partitions?

Also, would Ubuntu by default install itself in the same partition as the Vista partition?

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

It seems that article implies you shrink your current partition, and Ubuntu creates its own automatically?

---

### Post by bodhi.zazen on 2007-08-15
Use the Vista disk manager to resize your vista partition.

Leave the free space unpartitioned.

The Ubuntu CD will partition and format the unpartitioned space. It will not overwrite vista unless you tell it to so best look at Linux partitioning terminology :

Partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Install guide : [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by NonStop on 2007-08-15
So, assuming I shrink my Vista partiton (generally its by half), as [indicated here](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first), whcih step should I take from here:

> The first part of these options are a list of the hard drives that Ubuntu has detected. To use the guided partitioning select one of these and click Forward. The lower part of the list has an option to automatically use the largest area of free space, and an option for manually editing the partition table (with a graphical tool). The free space referred to in the former of these options is an area of a disk without any partitions on it. Please note that this is not the same as space that does not have any files in it. This option is for if you have made space on your drive before starting the installer, or if you are installing to a blank drive with no partitions yet.

[img]https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=5.png[/img]

Cheers.

---

### Post by Hobo Joe on 2007-08-15
You'd want to use the option that says 'use the largest continuous free space'.

But I still say that manuall partitioning is a safer option.

---

### Post by NonStop on 2007-08-15
I see, thanks.

---

