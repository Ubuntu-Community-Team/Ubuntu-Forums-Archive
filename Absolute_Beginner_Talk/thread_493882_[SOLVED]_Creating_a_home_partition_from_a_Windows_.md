---
title: "[SOLVED] Creating a /home partition from a Windows partition"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by nvteighen on 2007-07-06
Hi there!
Currently, I have a dual-boot system consisting in three partitions in the same hard disk:
1. WinXP NTFS
2. Ubuntu root partition
3. Swap

OK, in future I'd like to format the WinXP partition and transform it into a /home partition. I have thought on a possible way to do this, but I'd like to hear some more experienced users' opinions because I'm not sure if it's right or not. This is what I've planned:

1. Make a backup of my current /home folder (the whole thing, so I don't lose any configuration file).
2. Boot the PC with the Live CD.
3. Format the NTFS partition and make it be ext3
4. Delete /home folder's content from hard disk.
5. Copy the /home backup into the new partition.
6. Edit fstab so the new partition is automounts into /home (and backing the old fstab file up).

According to this, when I reboot from hard disk, the new partition should be mounted in /home with all files before the partitioning... And so, GNOME, OpenOffice, etc. configurations shouldn't get broken... Or yes???

---

### Post by Outrunner on 2007-07-06
You might want to try [this]("http://www.psychocats.net/ubuntu/separatehome") guide. Good luck and have fun ;)

---

### Post by HereInOz on 2007-07-06
That should work.  You may run into some issues with Grub, if you remove Windows but still leave Grub as the old dual boot configuration, but not too sure.

Worst case, you can always re-install Ubuntu in its original partition, making sure that you do not format the /home partition, and Ubuntu will pick up all your previous settings which were in the /home partion.

---

### Post by nvteighen on 2007-07-06
Thank you both!

I've thought about grub configuration and was going to ask about that. I'm going to look for that, because I want to avoid reinstalling Ubuntu unless there isn't another solution.

---

### Post by dptxp on 2007-07-06
If I were you I would backup data and make a totally fresh install with new partitions treating the HDD as a new one. It is worth the effort.

I would install Ubuntu and then kde-core.

One should anyway backup data.

---

### Post by nvteighen on 2007-07-06
> **dptxp said:**
> If I were you I would backup data and make a totally fresh install with new partitions treating the HDD as a new one. It is worth the effort.

I would install Ubuntu and then kde-core.

One should anyway backup data.

I'm taking notes of all opinions!

Thank you very much!

---

