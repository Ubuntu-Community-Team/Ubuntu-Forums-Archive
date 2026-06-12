---
title: "Should I start over? or is there still hope?"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by habtish on 2006-12-03
I had an 80GB HD with the following partitions
/dev/hdb1 - NTFS  , was using ntfs 3g to have RW access in essence "sharing" this space with XP
/dev/hdb2 - 10.6GB ext3 - ubuntu edgy (had been using it since breezy)
/dev/hdb3 - 433MB swap

So in all my stupidity, I wanted to have another ubuntu install to "test" things on w/o worrying about losing my current settings under my original ubuntu. I went and set a 5GB partition (Gparted) from the NTFS, which resulted in an "allocated" partition.

Installing Ubuntu... It showed the NTFS partition and hdb2.. me thinking the new partition I made (5GB unallocated) had been named hdb2 and my ubuntu partition hdb3, told the install program to use hdb2... Now that I am rebooting.. Grub only shows one Ubuntu install and there is only one Linux kernel under grub menu.lst

Did I just install edgy on top of my old install, hence losing everything I had?? Should the install script not have warned me about a bootable kernel being in the partition I am about to install and gave alternative? Why didn't the 5GB partition I made for this install not show up during the installation??

---

### Post by bulldog on 2006-12-03
If the partition was set to format during install I'm afraid it is gone.
Ubuntu will not install on a partition which has data on it,but if the format option was checked............it will indeed.

Sorry to say but I don't think it can be recovered easely.

---

### Post by Shatrat on 2006-12-03
Are you sure that your disk was successfully repartitioned?
Can you still see the 5 gig partition?
I'm not too familiar with the ubuntu installer since I've only used it once, but this is a good example of why it is wise to backup your home directory or have /home on a separate drive or partition.

---

### Post by habtish on 2006-12-03
> **Shatrat said:**
> Are you sure that your disk was successfully repartitioned?
Can you still see the 5 gig partition?

Yes, I can still see the 5GB partition,.. still listed as unallocated..

[quote=bulldog] If the partition was set to format during install I'm afraid it is gone.[/quote]
I unchecked the format from the swap, as I didn't want it to reformat that partition, but not the other partition.. I guess I Have lost everything... So if I am reinstalling and this time I want to give ubuntu more space than the current 11GB, how can I "merge" the 5Gb partition with the 11GB partition that is carrying my current fresh ubuntu install?

---

### Post by bulldog on 2006-12-03
If you download the Gparted live cd [25MB] and burn it to a disk,you can boot from it.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

This makes resizing and partitioning a lot easier.

---

### Post by habtish on 2006-12-03
> **bulldog said:**
> If you download the Gparted live cd [25MB] and burn it to a disk,you can boot from it.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

This makes resizing and partitioning a lot easier.
  I was using their Livecd all along.. I guess I can delete the current 11GB partition and make a new partition which includes the 5gb which is not being used now

---

### Post by Hoso001 on 2006-12-03
sorry wrong topic...

---

### Post by habtish on 2006-12-03
> **Hoso001 said:**
> sorry wrong topic...

Huh??

---

