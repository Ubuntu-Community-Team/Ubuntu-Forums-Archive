---
title: "E: &amp; F: FAT32 drives dissapeared!"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by sifar786 on 2006-10-08
Hi all,

I have a PIII 700MHz Desktop PC & 40GB HDD on which i had installed Winxp pro. 

I had the following FAT32 partitions each was of **10GB **size:
(primary)C:, (logical)D:, (logical)E:, (logical)F:

There was very little space left on each logical partition(approx on each) 1GB on c:, 1.5GB on d:, 2GB on e: & 1.5 on F:. On each partition, except the C: drive, i had a lot of mine & my brother's work files (lot of data in GB's).

Once i received the Ubuntu Desktop CD, for test purpose, i tried installing it as per the instructions. It was very good & i was told that it would automatically manage the spaces on my partitions & will create ext2fs partitions using the free space. It did!

There were 2 partitions created automatically, 1 - ext2fs of 4.3 gb (approx) & the other of 226MB (swap).

Now, since i got a dual boot OS, GRUB was loading Ubuntu correctly, but when i tried Windows XP, it loaded it, but now the space was neglible & since my brother also uses it, i had no option but uninstall Ubuntu after going thru instructions given by a Ubuntu linux user on his website.

He had adviced to boot from Winxp & go into restore mode & then do FixMBR to replace GRUB loader with that of winxp. It did that & then i was adviced to use DiskManagement from Control panel to delete the Linux (Unknown) partitions. 

As soon as i deleted only the 226MB swap partition, my E: & F: partition automatically disappeared & now DiskManagement showing as 226MB free partition & 18.65GB free partition + there is an Unknown partition of 4.34GB. I have not deleted this partition but had deleted only the swap partition.

1] Has all my data on those drives been deleted? i have not yet gone & given the free spaces a drive letter name or formatted them as i want some expert advice & also am afraid, doing so would reduce the chances of getting my data back or restoring the E & F partitions.

2] how do i bring back the E & F FAT32 partitions along with the complete data on them?

Please advice asap.

Best regards,

Sifar

---

### Post by CatKiller on 2006-10-08
I think that instead of deleting the swap partition you may have deleted the Extended partition that contained all the Logical drives. I believe that it is in principle possible to "redraw" the partition table around the data that still exists on the drive, but I don't know how to do this.

Before you do anything else, make an image of the drive (including the unpartitioned space) on a new drive, so that you don't make it worse.

---

