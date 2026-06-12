---
title: "uninstalling..."
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by natural_orange on 2006-11-30
I have had Ubuntu for a couple of months dual-boot on another computer i have that isn't connected to the internet and i really have no use for it anymore and would like to uninstall it.  After i get internet in there i may reinstall Ubuntu.

How do i go about removing Ubuntu.... 

I can reset the MBR using a winxp disc i have because I've done it already when i had problems with GRUB.

How do i reformat the harddrive to FAT32 or NTFS?

---

### Post by CatKiller on 2006-11-30
If you're planning on installing Windows on there, then you don't need to bother - that process will wipe out anything you have on the drive.

---

### Post by LLRNR on 2006-11-30
If you have the XP install disk, insert it in your cdrom drive, boot from it and choose recovery console mode. After you "**fixmbr**" as you say you already did, at the recovery console prompty, type "**diskpart**" to (re)create your partitions - you need this for having a letter assigned to the desired partition(s). After this stage, you can simply **format c:** (d:, e:, ...).

LLRNR

---

### Post by natural_orange on 2006-11-30
I already have WinXP on another HD. I just need to make the HD that i have Ubuntu on something that WinXP can use.

---

### Post by natural_orange on 2006-11-30
will doing the **diskpart** screw up my existing HD?

---

### Post by LLRNR on 2006-11-30
No, **diskpart** will just show you what partitions you have. If they already are FAT and/or NTFS, it will show them as they are (with their corresponding drive letters), and partitions which have other filesystems (like ext3 for instance) will appear like "unknown something" if I remember well. You don't have to mess with the partitions you want to keep (the fat/ntfs ones), you'll just have to make a new partition for the ext3 ones and then format them for fat / ntfs filesystems. (You can use *format /?* for more info).

LLRNR

---

### Post by bulldog on 2006-11-30
Just use the live cd or download the gparted live cd [25MB]

Burn the gparted live cd to a cd-r and boot from it.
Select the disk you want to reformat and do so.
You can download the gparted live cd here,

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by natural_orange on 2006-11-30
Ubuntu made a partition on the hard-drive for the swap memory, can i can combine the two into one partition? can do that in **diskpart** ?

---

### Post by natural_orange on 2006-11-30
I have an Ubuntu (dapper drake) live cd.  Can i use that to reformat?

im trying to [ext3(0) + ext3(1)] ---> fat32(0)

---

### Post by LLRNR on 2006-11-30
As far as I remember, yes, every partition you have will show up, if it's FAT or NTFS it will appear as FAT or NTFS and if it's something else, like ext2, ext3, ReiserFS etc, it will appear (*each* of these unhandled partitions) with its actual size and as an unknown type. You'll have to press a key ('d' if I remember well) to delete that partition, it will add up to a general "unused space" thingy and then you can take up your new unused space, repartition it (for instance you can gather all the ext3 partitions you might have now under one big new partition), it'll be assigned a drive letter (say **e:**) and then you can just **format e:** - the default is NTFS, if you want your new e: to be FAT just go and type **format /?** to see more info.

LLRNR

---

### Post by natural_orange on 2006-11-30
Allright....im gonna go give that a try...ill come back if have any problems.

---

