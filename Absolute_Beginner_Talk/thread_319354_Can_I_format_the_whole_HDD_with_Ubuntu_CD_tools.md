---
title: "Can I format the whole HDD with Ubuntu CD tools?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by geezas on 2006-12-15
I just burned myself an Ubuntu 6.06 CD.  I want to format hdd, maybe make two partitions.  And then I want to install Ubuntu on a clean, empty HDD.  Can I do that using the CD or do I need to have some kind of floppy disk with the required tools?

...also, what file system does Ubuntu use? Fat? NTFS? Other?

Thanks for help...

---

### Post by Sqwishy on 2006-12-15
> **geezas said:**
> I just burned myself an Ubuntu 6.06 CD.  I want to format hdd, maybe make two partitions.  And then I want to install Ubuntu on a clean, empty HDD.  Can I do that using the CD or do I need to have some kind of floppy disk with the required tools?

...also, what file system does Ubuntu use? Fat? NTFS? Other?

Thanks for help...
hehehe... Ubuntu has tools built in with the installer for formatting and partitioning your hard drive

It doesn't use Fat or NTFS ... those are windows filesystems. You should use ReiserFS it's best in my oppinion

---

### Post by raul_ on 2006-12-15
You can edit/format your partitions with Ubuntu Live CD.
Linux uses ext file system (ext3 at this point)

---

### Post by raul_ on 2006-12-15
> **Sqwishy said:**
> It doesn't use Fat or NTFS ... those are windows filesystems. 

That's not true

---

### Post by taurus on 2006-12-15
If you download the desktop CD/LiveCD, there is a gparted in the System menu that you can use to resize your harddrive.  But do not install Ubuntu on fat32 or ntfs because it's not going to work.  Use the default filesystem which is ext3 because that's what most people use...

---

### Post by geezas on 2006-12-15
**Follow up question:**

Do I have to reformat my HDD before starting with the installation, or will I be able to do that once I start it?

...and what file system is the best? ...or what are the cons and pros of each?

---

### Post by lyceum on 2006-12-15
> **geezas said:**
> **Follow up question:**

Do I have to reformat my HDD before starting with the installation, or I will be able to do that once I start it?

...and what file system is the best? ...or what are the cons and pros of each?

You should be able to do this in one swoop. The last part of the setup is the partition. Just go to advanced and set it up however you need it.

---

### Post by raul_ on 2006-12-15
You'll be able to do that once you start the installation.

About the file systems, well....that would need pretty much a college class to explain :rolleyes: but stick to ext3 because Linux won't work with no other

---

### Post by poohbear1616 on 2006-12-15
Another important question is if your going to dual boot or use the hole drive. Dapper installer does an excellent job of handling the partitions by default either way, Unless your wanting to get your hands dirty for the experience.

---

### Post by poohbear1616 on 2006-12-15
> And then I want to install Ubuntu on a clean, empty HDD.

ooops...didn't pay attention to that.

---

### Post by mcduck on 2006-12-15
> **raul_ said:**
> You'll be able to do that once you start the installation.

About the file systems, well....that would need pretty much a college class to explain :rolleyes: but stick to ext3 because Linux won't work with no other

Linux can work with plenty of file systems, all with different pros and cons. But for home use Ext3 is a good choice.

---

