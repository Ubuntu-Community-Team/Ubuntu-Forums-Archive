---
title: "Problems with read/write to hdds"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by michaelof36 on 2007-05-05
I installed the NTFS Configuration Tool and I am still unable to write to NTFS drives including external. It syas it was unable to remount forcing me to disable the tool and restart to gain access again. I really need to be able to write to my ntfs drives to share info between WIn XP and Ubuntu as well as my Mac at work. Anybody have any suggestions as to getting around this?

PS. this is what it gave me when I inserted my flash drive

Mike

---

### Post by crispy_420 on 2007-05-05
Easiest option:

Use fat32 to share data. As long as a file is not over 4GB, it won't make a difference.

---

### Post by michaelof36 on 2007-05-05
My windows partition in formated in ntfs is there any other way to read and write to at least this partition?

---

### Post by crispy_420 on 2007-05-05
There are NTFS drivers, can't remeber the names right now. Do a search in synaptic for NTFS. After installing you'll need to mount the drive or add to fstab. People claim they are stable and will cause no hard. But be very cautious.

---

### Post by Michaelt74 on 2007-05-06
This is a summarised howto, check out the 'Mount Windows' section.

[http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/](http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/)

---

### Post by Lucifiel on 2007-05-06
Oh, I got the same issue as you yesterday.

Here're a few workarounds:

1) Boot into Windows twice and shut down properly.

2) Run chkdsk from windows on ALL the affected volumes. That is: the ntfs volumes or drives that you can't mount.

3) Eject an external usb drive within Windows.

---

