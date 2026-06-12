---
title: "Need help with partitioning"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-10-09
I am trying to install Ubuntu Dapper on a Dell laptop and am getting stuck in the partioning stage. I need some advice on the matter.

When I come to the partition stage, it does not give the option of “Resize IDE1 master, partition #1, and use free space”. Instead it gives the option of “Use the largest free contiguous space”. And when I choose that, a message flashes saying “unable to do partitioning”.

When I tried partitioning manually, my hard disk shows this structure:

FAT 16, NTFS, unallocated, FAT 32, unallocated (in that order)

The problem with this is the following:

1. There are already three primary partions: FAT 16, NTFS, and FAT 32. I can create only one more primary partition.

2. The two unallocated free spaces are not contiguous.

Therefore I can not have a “/” mounting and a “swap” in the end, or wherever. I think it is because of this that the installation is unable to do partitioning.

I was thinking of doing the following: deleting the FAT32 partition and then going back and choosing the “Use the largest free contiguous space” option. Will that work? Or should I do something else?

Thanks.

---

### Post by CatKiller on 2006-10-09
Depending on how large your blocks of unallocated space are, you could put partitions in them, were it not for the fact that you've already got three Primary partitions.

You can use the manual partitioning tool (gparted) to move the FAT32 partition so that you have a big block of free space to put one more partition in. Make this an extended partition, and you should be able to put up to 60 or so logical drives in there. Two should be sufficient, though.

EDIT: This shouldn't be taken as advice on what you **should** do, just as an indication of what you **could** do. What you decide to do ultimately depends on how valuable that FAT32 partition is to you, and how much space you want to allocate for Ubuntu.

---

### Post by aam-aadmi on 2006-10-09
Can I just delete the FAT 32 partition if I don't want to keep it? So, here is what I want to do:

1) Choose to edit the partition table manually;
2) delete the FAT 32 partition
3) save changes, and return to the first step
4) choose "use largest contiguous space" to install Ubuntu.

Will this work? I want to devote all my free space to Ubuntu linux.

---

### Post by CatKiller on 2006-10-09
Yes, that should work a treat.

---

