---
title: "gparted"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by sabatron on 2008-02-15
So I'm a bit confused about this resizing partitioning thing.  I attached a screenshot of my gparted.  My 4 partitions are swap (1gb), the very large one is windows, and the other 2 are ubuntu I think.  I'm not quite sure what the ext3 is but I'm affraid of deleting it in case it has something important.  I just wanted to know how I can get my 12 gigs of unallocated space to go into my fat32?  I made the ext3 smaller so it took the 12 gigs out of there but now I don't know what to do with it.  I'd like to put it into my fat32 so I can copy my WoW files from hda1 to hda2.  Also, aren't I supposed to only have 3 partitions?  1 for windows, 1 for ubuntu and 1 for swap?  I don't know how I ended up with this set up but the good news is I didn't lose any data...just hardrive space.  Thanks

---

### Post by jken146 on 2008-02-15
You can't combine the empty space with the FAT32 partition, as they are not next to each other on the disk.  You don't need to do this though, as Ubuntu can write to NTFS partitions.  If you are using Gutsy, you don't have to do anything to enable this.

The ext3 partition is mounted on /, which is the root directory of the Linux file system.  This is where Ubuntu lives.  If I were you, I wouldn't make it any smaller than it is now.  The swap partition is virtual memory for Linux (Windows has this sort of thing too but includes it in the same partition as its systme files).

You can do 2 things with the empty space -- add it to your ext3 partition or create a new partition there.

---

### Post by PinkFloyd102489 on 2008-02-15
I personally havent seen an option to do so. You might be able to move it with gparted.

---

### Post by MasterJS on 2008-02-15
Normal ext3 is the file system format that Linux uses, instead of the NTFS or FAT32 that is normal in Windows. I'm guessing you set up your Ubuntu to use FAT32, am I right? And to use that unallocated space you need to reformat your partitions. If you want to add it to the Windows partition, you need reformat it to use all of the remaining space, meaning its going to use those 12 GB you removed. Or if you want to create a separately different partition, you'll need to format it into its on partition. Now the thing is that Windows does not read ext3 partitions, you need a special program for that which I don't know its name. I read about somewhere but I completely forgot its name. So what Windows uses is NTFS or FAT32, normally. Ubuntu can read all these, thats the great thing about Linux. So if you make a separate partition out of all of those 12 GB, it'd suggest formatting it to NTFS as FAT32 has the 4 GB file limit. Yes, that's right. FAT32 is a file system with a limit to which the file size can be.

---

### Post by sabatron on 2008-02-15
I think I was confused,..I thought I had to copy my WoW folders from hda1 to hda2(fat32) but I actually need to copy them from hda1 to hda3(ext3)?  In that case, I don't need to resize...because I'm pretty sure WoW is less than 18 gigs.

PS hda1 and hda2 were the 2 icons that were on my desktop when i installed Ubuntu.  I don't know if that helps figure out what one is wich

---

### Post by jken146 on 2008-02-15
> **MasterJS said:**
> Normal ext3 is the file system format that Linux uses, instead of the NTFS or FAT32 that is normal in Windows. I'm guessing you set up your Ubuntu to use FAT32, am I right? And to use that unallocated space you need to reformat your partitions. If you want to add it to the Windows partition, you need reformat it to use all of the remaining space, meaning its going to use those 12 GB you removed. Or if you want to create a separately different partition, you'll need to format it into its on partition. Now the thing is that Windows does not read ext3 partitions, you need a special program for that which I don't know its name. I read about somewhere but I completely forgot its name. So what Windows uses is NTFS or FAT32, normally. Ubuntu can read all these, thats the great thing about Linux. So if you make a separate partition out of all of those 12 GB, it'd suggest formatting it to NTFS as FAT32 has the 4 GB file limit. Yes, that's right. FAT32 is a file system with a limit to which the file size can be.

Do not format anything!  You will lose data!

As for which partition is which, look at your screenshot.

---

### Post by MasterJS on 2008-02-15
As said before, the best thing he could do would be to turn that unallocated space into another partition just for the files, basically creating a space between Ubuntu and Windows where he can access files from both areas. This COULD be a good idea.

---

### Post by sabatron on 2008-02-15
She* can't have more than 4 partitions

---

### Post by MasterJS on 2008-02-15
Mmm no wonder, the swap is not an extended partition. Well, have you tried reallocating that space back into one of the partitions?

---

### Post by sabatron on 2008-02-15
So I talked it over with my buddy Mike...and apparantly the new version of Ubuntu (7.10) allows you to run WoW from your windows drive (ntfs-3g)...so I think I'm just gonna burn a LiveCD real quick, partition over ext3, and start from scratch.

---

### Post by Miljet on 2008-02-15
The FAT 32 partition is probably a recovery partition for Windows. That is how my disk is set up. If so, you don't want to do anything with it, unless you decide to do away with Windows.

---

### Post by regbsn on 2008-03-03
n00b here (fair warning),

Could the FAT 32 be combined with the NTFS (Windows) partition? If so, then the unpartitioned area could be a "/ home" partition?

Do you really need a recovery partition if you just do a disk image or recovery disk or the restore disk from when you bought the computer? How ofter if ever does the recovery partition update?
I never had a Recovery partition until I bought a XP MCE laptop last year.

From what I have been reading,  a "/ home" partition is a good idea to protect your data and settings/preferences in case you update or grenade your Linux OS partition (ext3).

Yes/no?

Please correct me if I am wrong. :-k

---

### Post by regbsn on 2008-03-29
*Bump*
:):):):)

---

