---
title: "Partition Editing"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by kevCast on 2007-06-02
I'm trying to use the default partition editor on the install ISO CD for Ubuntu to override my current Ubuntu partition manually. How would I go about doing this? I tried to delete the partition and set-up my own ext3 partition, but it tells me I have no root file system defined. I'm not really so sure either about the meaning of primary or logical partition, or about where the partition should start (beginning, end). The mount point is /media/hda2 and the current device ID is /dev/hda2.

---

### Post by raja on 2007-06-02
You should either use the automatic partitioning method (it will delete all the partitions on the drive and partition it automaticaly) or, if you want to do it yourself, read a bit about partitioning. There is not enough space here to explain all that you asked.

---

### Post by plcdfa on 2007-06-02
> **kevCast said:**
> I'm trying to use the default partition editor on the install ISO CD for Ubuntu to override my current Ubuntu partition manually. How would I go about doing this? I tried to delete the partition and set-up my own ext3 partition, but it tells me I have no root file system defined. I'm not really so sure either about the meaning of primary or logical partition, or about where the partition should start (beginning, end). The mount point is /media/hda2 and the current device ID is /dev/hda2.

Do you want to do a clean reinstall over your existing ubuntu version?

---

### Post by locke.dragon on 2007-06-02
i've tried doing what you're attempting and it's impossible in the ubuntu live cd.  you'll have to use the gparted live cd.  it's got a simple interface, but it gets the job done quickly and efficiently, plus it's never screwed up for me (and i've done EXTENSIVE partition editing with it).  and what exactly are you hoping to accomplish?

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by kevCast on 2007-06-02
> **plcdfa said:**
> Do you want to do a clean reinstall over your existing ubuntu version?

Yes.

---

### Post by ugm6hr on 2007-06-02
> **locke.dragon said:**
> i've tried doing what you're attempting and it's impossible in the ubuntu live cd.  you'll have to use the gparted live cd.  it's got a simple interface, but it gets the job done quickly and efficiently, plus it's never screwed up for me (and i've done EXTENSIVE partition editing with it).  and what exactly are you hoping to accomplish?

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Or reformat the old Ubuntu partition from the new LiveCD. In Terminal (assuming Ubuntu is currently on /dev/hda2):
mkfs.ext3 -c /dev/hda2

You should then be able to manually install the new Ubuntu into the same partition (as /).  Your swap partition should remain the same.

---

### Post by kevCast on 2007-06-02
> **ugm6hr said:**
> Or reformat the old Ubuntu partition from the new LiveCD. In Terminal (assuming Ubuntu is currently on /dev/hda2):
mkfs.ext3 -c /dev/hda2

You should then be able to manually install the new Ubuntu into the same partition (as /).  Your swap partition should remain the same.

[[IMG]http://img364.imageshack.us/img364/8192/screenshotus1.th.png[/IMG]](http://img364.imageshack.us/my.php?image=screenshotus1.png)

---

### Post by ugm6hr on 2007-06-02
Try sudo.

sudo mkfs.ext3 -c /dev/hda2

---

### Post by candtalan on 2007-06-02
Do you want to do a clean reinstall over your existing ubuntu version?
> **kevCast said:**
> Yes.

I have had trouble (this very day) using the live CD installer with manual partitioning choice for a similar thing as you wish.

However, the live CD - when up an running - has a suitable and very good partition editor (in the System menu list). I did not go into the installer, I first used the partition editor in the live cd to delete create and format the various partitions to my requirements. 

I then subsequently used the live cd installer, manual install choice, and it was easy to be successful in allocating the existing new partitions  for my install.

I concluded that the live CD installer (manual choice) had some problems.

hth

---

### Post by locke.dragon on 2007-06-02
i've found that an easier method is to use the gparted live cd to delete the ubuntu partitions including the extended one most likely surrounding it AFTER backing up your data.  then  just let the ubuntu live cd install in the "larges free contiguous space."  that's how i last did a clean re-install.  works like a charm.  :D

---

