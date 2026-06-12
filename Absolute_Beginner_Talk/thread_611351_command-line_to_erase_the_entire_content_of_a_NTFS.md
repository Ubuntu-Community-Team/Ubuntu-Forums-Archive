---
title: "command-line to erase the entire content of a NTFS formatted partition?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-11-12
hey all.

i'm trying to figure out the command-line way to delete the entire content of a NTFS formatted partition, without deleting the partition itself (this is step1 of an restoration sequence, step 2 is rebuilding the content from a saved image). i've tried the fdisk help menu, because i think that's going to be the tool to use. but have only found options to delete a partition or change its size.

i'm wanting to keep the partition itself in tact. just wipe all the files from it.

thanks!

---

### Post by taurus on 2007-11-12
Why not use gparted to reformat that partition.  Then, everything will be gone but you still have the same partition as ntfs filesystem.

---

### Post by Whiffle on 2007-11-12
rm -rf /media/path/to/partition/*

---

### Post by ijason on 2007-11-12
**@ whiffle **: bingo! thanks. :) is there an easy, and command-line, way to mount an NTFS partition in ubuntu as read/write? it seems to only be able to mount NTFS as read only?

---

### Post by rsambuca on 2007-11-12
With Gutsy, ntfs is read/write by default.  If you are not using gutsy, then just 

sudo apt-get install ntfs-3g ntfs-config

---

### Post by ijason on 2007-11-12
**@ rsambuca** : will this mount NTFS drives as read/write from now on? or is it a program i'll need to run to get them mounted that way? :)

---

### Post by rsambuca on 2007-11-12
ntfs-3g is the driver to allow you to write.  The ntfs-config is the gui app to set things up for you.

---

### Post by ijason on 2007-11-12
thanks! i'll give it a shot

---

### Post by ijason on 2007-11-12
hmm. ntfs-config popped up a little window, and i checked to enable support for external NTFS drives (odd, i couldn't check the option for internal drives, but i didn't have any mounted at the time). and i still get the 'read only OS' error code when i try to remove files from the drive.

i tried unmounting and then remounting the drive, and same results. do i need to restart ubuntu?

---

