---
title: "Corrupt GPT Table on Macbook"
date: 2015-12-11
forum: Apple Hardware Users
---

### Post by tristan-massey1 on 2015-12-11
Hello,

I'm hoping that someone here can assist me with a partition table problem I am having.

I installed Ubuntu 14.04 on my Macbook 11,1 by shrinking the Mac HD partition by 50GB and installing in that empty space. Everything was going smoothly until I decided I wanted to upgrade to 15.04 due to compatibility issues with themes. I attempted an update with Software Updater, which failed and said my OS may be unbootable. Sure enough, I could not boot back into it (just a blank purple screen).

To fix the strange booting issue, I thought I could just delete that partition and the 50GB would return to empty space. I got Ubuntu on a USB and used GParted to delete the partition, which returned it to "unallocated space."

I went back to Mac OS to try to re-allocate the two partitions back into a single 250GB Mac OS partition, but disk utility didn't see the other 50GB. It's as if it disappeared. I click on the name of the 250GB hard drive (not the Mac HD partition) and the bar is completely filled with the Mac HD partition, saying 200GB next to it. It says the same thing if I boot into recovery mode first.

I can still see the unallocated space with GParted, but when I first open GParted it gives me an error message saying my primary GPT table is corrupt, and that it's using the backup. If I run gdisk, it detects no issues automatically and displays the GPT as "present" along with the MBR as "hybrid." I don't entirely know how to use this program, so its very possible I'm not using it correctly.

My goal is the following:
I need to fix my GPT table (probably, I don't know if this is actually causing any issues, but GParted tells me it's corrupt) and restore the two partitions to a single 250GB partition, so I can start fresh and reinstall Ubuntu.

I am totally open to wiping the whole drive and starting fresh with both operating systems (I have backups of all my important files) but I also probably need the Mac Recovery and EFI boot partitions, I don't want to destroy those.

Thank you for any help you provide, I am very new to all this information.

EDIT: I am now able to view the missing 50GB in Mac OS after creating a partition with it in GParted (it can see the partition, just not the empty space for some reason). When I try to join them together to 250GB it fails, and says "You can't perform this resize unless it has a booter (target partition is probably too small)." This is probably an artifact of the corrupt partition table? If anyone has any advice on fixing it, help would be greatly appreciated, thanks!

---

### Post by oldfred on 2015-12-12
I do not really know Mac.
But with a Mac the hybrid partition was created to allow you to boot Windows.
Macs use UEFI & gpt partitioning, but older Windows only booted in BIOS mode and had to have MBR partitioning.
So they created the hybrid partition where the first 4 primary MBR partitions and the first 4 gpt partitions would be sync'd. Windows then could be installed into one of the MBR partitions and the Mac would use the gpt partitions.
The recommendation is to avoid hybrid partitions at all cost. And Ubuntu works with gpt. I  think the new Windows can be now installed in UEFI on Mac but not sure. Or you do not need hybrid.

It sounds like you created hybrid partitions, and now they are out of sync.
       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

If you have or want Windows older versions that only boot in BIOS mode then you may need to resync using your Mac tools and/or repair partitions. Otherwise I would just eliminate the MBR/msdos partitioning. All gpt disks have the MBR, but it normally only has one entry saying drive is gpt, so old msdos tools do not try to partition a gpt drive incorrectly.

---

