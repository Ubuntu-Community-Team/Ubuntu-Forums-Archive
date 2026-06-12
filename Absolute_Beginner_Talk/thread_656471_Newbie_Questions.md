---
title: "Newbie Questions"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by mjheagle8 on 2008-01-02
I am interested in installing ubuntu as a dual boot on my pc.  I have 512 meg of ram, 2.6ghz celeron, and 80 gb hard drive.  I have an old ubuntu 6.06 disc from last year.  I have a few questions.  

1.  I want to install by making a new partition in free space.  However, I currently cannot do this.  I looked at a map of my drive and data is scattered all over, which would explain why.  I am only using 26gb on my drive.  How can I fix this problem?  I don't have any other hard drives to use for backup.
2.  How would I make music and pictures available to be read by both windows and linux?
3.  I have an encrypted wireless network witha a security passcode.  Will I be able to access in linux?  How?

Thanks for your help!

---

### Post by orro_xo on 2008-01-02
1. You should do a defragmentation of your harddrive and then you must free ("unpartition") the unused harddrive.
2. You could have your music and images on the windows partition since you can install support for ntfs in linux. This is easier than the other way around.

---

### Post by nathandelane on 2008-01-02
> 1. I want to install by making a new partition in free space. However, I currently cannot do this. I looked at a map of my drive and data is scattered all over, which would explain why. I am only using 26gb on my drive. How can I fix this problem? I don't have any other hard drives to use for backup.

To do this, start out in Windows and defragment your drive. Open up My Computer, right click on your hard drive, and click on Properties, then click on the Tools tab and start the defragmenter tool.  Once that has finished, you may want to run checkdisk on it, so open up a command prompt, by going to Start, Run, type cmd, click on OK, then type:

chkdsk /F

You will be told that it cannot run right now because the drive is in use, and you will be asked if you want to run it on the next reboot. Answer Y (yes) to this question. Then reboot your computer and let Checkdisk fix anything it finds.

After that, you'll need to boot up Ubuntu, resize your hard drive partition, and create at least two new partitions, one ext3 format for your files system and one Linux Swap format (usually 2x your ram) for swap space.  Write those changes, then install using those partitions.

> 2. How would I make music and pictures available to be read by both windows and linux?

To do this you could make a FAT32/VFAT partition on your hard drive exclusively meant to store your media, then both Linux and Windows can read and write to it.

> 3. I have an encrypted wireless network witha a security passcode. Will I be able to access in linux? How?

Ubuntu makes this fairly simple, especially if your wireless router is standalone - you'll simply access the same way you do in Windows (usually via a web interface), if it is part of your computer, then when you install Ubuntu, there will probably be an icon in the top right (if your using GNOME Desktop) that will indicate what network connections you have available and wireless will be one of them. If this isn't the case, then poke around the FAQs or online just google for information on your particular model.

Does that help?

Nathan

---

### Post by p_quarles on 2008-01-02
I would strongly recommend against editing your partition table if you don't have a way to backup your data. Not having backups is very risky by itself -- adding a somewhat risky procedure (partitioning) to the mix is a bad idea.

---

### Post by nathandelane on 2008-01-02
True as it is p_quarles, editing your partition table is the only way to dual boot Windows and Linux with a single hard drive.  Also as long as you run defrag and chkdsk on your disk first, there is a smaller chance of losing or corrupting data.  I have done this hundreds of times and have never experienced any problems.  Another thing to note is the ntfsresize, which is what qtparted and parted use to resize ntfs partitions is a very mature project. There is really very little to worry about ultimately.

---

### Post by p_quarles on 2008-01-02
> **nathandelane said:**
> True as it is p_quarles, editing your partition table is the only way to dual boot Windows and Linux with a single hard drive.  Also as long as you run defrag and chkdsk on your disk first, there is a smaller chance of losing or corrupting data.  I have done this hundreds of times and have never experienced any problems.  Another thing to note is the ntfsresize, which is what qtparted and parted use to resize ntfs partitions is a very mature project. There is really very little to worry about ultimately.
Yes, partitioning a hard drive is relatively safe. Not having backups is the risky part, and I stand by my advice that one should not attempt to partition a drive without backing up any important data first.

---

