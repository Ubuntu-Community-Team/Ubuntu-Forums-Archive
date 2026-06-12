---
title: "OSX, Ubuntu, then Windows"
date: 2007-05-16
forum: Apple Intel Users
---

### Post by drspangle on 2007-05-16
Hi all.

I have a macbook wth OSX and Ubuntu 7.04 installed after using bootcamp.

I need Windows (be in XP or a copy of Vista Business floating around) for some university work but I`m worried about the install process.

What`s the best way of going about doing it? Will windows show up on the bootcamp menu or will I have to use the grub menu to boot it?

I can`t risk losing my ubuntu partition.

Thanks

---

### Post by benanzo on 2007-05-16
The install shouldn't be too hard.   you will need to use the third-party EFI bootloader "refit" [http://refit.sourceforge.net](http://refit.sourceforge.net) as the boot menu because the Apple EFI boot menu only supports two menu options.

 The first trick I'll tell you is that you need to temporarily format the 200MB fat32 partition that OS X created as the first partition (OS X doesn't even use it) as something other than Fat32 or NTFS before you run the Windows installer and then format it back to fat32 after you're done.  You should use parted or Gparted to make the windows partition as NTFS (if that's what you want) or fat32 also before you run the windows installer.  That way you will *guide* windows into using the partition that you want for C: rather than the 200mb fat32 partition (which windows will default to if it can't find anything better)  and since it knows nothing of ext3 or hfs+, it will just refuse to install without formatting your drive.

After the install just run the partitioning tool at the refit boot screen (gptsync) and windows will show up in the menu.

---

### Post by drspangle on 2007-05-16
> **benanzo said:**
> The install shouldn't be too hard.   you will need to use the third-party EFI bootloader "refit" [http://refit.sourceforge.net](http://refit.sourceforge.net) as the boot menu because the Apple EFI boot menu only supports two menu options.

 The first trick I'll tell you is that you need to temporarily format the 200MB fat32 partition that OS X created as the first partition (OS X doesn't even use it) as something other than Fat32 or NTFS before you run the Windows installer and then format it back to fat32 after you're done.  You should use parted or Gparted to make the windows partition as NTFS (if that's what you want) or fat32 also before you run the windows installer.  That way you will *guide* windows into using the partition that you want for C: rather than the 200mb fat32 partition (which windows will default to if it can't find anything better)  and since it knows nothing of ext3 or hfs+, it will just refuse to install without formatting your drive.

After the install just run the partitioning tool at the refit boot screen (gptsync) and windows will show up in the menu.

Forgot to mention I was using refit already. So it is that simple? I already have a fat32 drive for sharing between linux and osx at the end of the drive - will this be a problem?

/Edit

I need to make a driver cd also, how can I trick bootcamp into letting me do this without losing my partitions?

---

### Post by benanzo on 2007-05-17
You can stop the Bootcamp wizard after creating the driver CD by just closing the program and not continuing with the partitioning.  It is strongly advised NOT to let Bootcamp try to partition your disk.  You can either use OS X's diskutil or partition it from the Ubuntu LiveCD with GParted (which I think is much easier.)

---

