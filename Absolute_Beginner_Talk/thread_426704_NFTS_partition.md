---
title: "NFTS partition"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by dmg025 on 2007-04-28
I recently created an nfts partition in my ubuntu drive so that I can share and edit media files accross windows and ubuntu and have one common place for my itunes library.  My problem is that when I try and add media to the drive (which is mounted and visible on my desktop) it tells me I do not have permission to add the files.  How do I change the permissions to this drive (its called 'disk') on my desktop

Thanks in advance
DMG025

---

### Post by taurus on 2007-04-28
You need to use/install ntfs-3g driver if you want to write to ntfs filesystem.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by SendDerek on 2007-04-28
This is an easy one...

You'll need the NTFS-3G package.

Here's a good how-to:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by orb9220 on 2007-04-28
You need to install the ntfs-3g to allow writing to ntfs. Default install only allows reading mounted ntfs partitions.

---

### Post by az on 2007-04-28
You can also install the ext2/ext3 driver in windows.  That way, you don't need a seperate partition to share files between OSes.  Windows will see your ext3 partition as a native windows partition.

fs-driver.org

---

