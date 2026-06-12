---
title: "Help on how to free space on partition"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by mason215 on 2008-02-08
I am new to linux and thought it would be a great idea to dual boot windows and ubuntu. But it seems that my hard drive won't let me. Next to the used and unused(in the partition editor) it has lines like: --- --- boot. I have no idea what this means and it won't let me add more then 7 megabytes to free. And i was wondering what to do. thanks

---

### Post by talsemgeest on 2008-02-08
Could you please attach a screenshot of the problem? That will help a lot towards figuring what the problem is.

---

### Post by billgoldberg on 2008-02-08
> **mason215 said:**
> I am new to linux and thought it would be a great idea to dual boot windows and ubuntu. But it seems that my hard drive won't let me. Next to the used and unused(in the partition editor) it has lines like: --- --- boot. I have no idea what this means and it won't let me add more then 7 megabytes to free. And i was wondering what to do. thanks

Ok, you'll going to have to partition your hard-drive before installing ubuntu.

There is a nice littel live cd for this called [gparted]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828")

You would burn that the same way you burned ubuntu.

A guide to using it is[ here]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") (lots more on google).

This should do the trick.

You can than select the second partition to install ubuntu onto.

(note: it's always adviced to back up important data before doing this. Not to scare you, but lets you the computer lost power during partitioning, the hard drive could become corrupted)

---

### Post by talsemgeest on 2008-02-08
Gparted is already on the ubuntu live cd.

Simply go to system>administration>partition editor.

Saves burning another cd anyway...

---

### Post by mason215 on 2008-02-08
[http://img171.imageshack.us/img171/5769/screenshotdevhdagparteddj5.png](http://img171.imageshack.us/img171/5769/screenshotdevhdagparteddj5.png)

there you go.

---

### Post by Moop on 2008-02-08
You need to click on and highlight your ntfs partition. That's the /dev/hda2 partition. Then click on resize and you should get the option to resize it. 

The first partition is likely a hidden partition for restoring Windows.

---

### Post by mason215 on 2008-02-08
> **Moop said:**
> You need to click on and highlight your ntfs partition. That's the /dev/hda2 partition. Then click on resize and you should get the option to resize it. 

The first partition is likely a hidden partition for restoring Windows.

I did this, but it wont let me free over 7 megabytes for some reason. 

heres another screenshot its the first window i don't get it

[http://img512.imageshack.us/img512/6139/screenshotvl4.png](http://img512.imageshack.us/img512/6139/screenshotvl4.png)

---

### Post by mason215 on 2008-02-08
bump

---

### Post by lswest on 2008-02-08
have you defragmented the drive before trying to resize? and if you're running vista, you can resize the partition using the vista partitioning tool under computer-->manage-->hard disks
basically you just need to create free space to partition

---

### Post by talsemgeest on 2008-02-08
You can try removing the boot flag. Click on the line with the boot flag and go to partition>manage flags and unselect "boot". BTW, the ... means that gparted cant see any data on the partition

---

### Post by mason215 on 2008-02-08
thanks for the suggestion, but it seemed that it didn't do anything. But there is some kind of warning about cluster accounting failing... i posted a picture in one of my posts above(its the first window on top)

---

### Post by talsemgeest on 2008-02-09
Will it let you scan the ntfs partition for errors?

---

### Post by Bartender on 2008-02-09
I'd try downloading/burning the latest version of GParted LiveCD (GPLCD), as was suggested earlier, rather than using GParted on Ubuntu LiveCD.  The dedicated partitioner seems to give better results than the version included on Ubuntu disc.
Burn it slowly, use a good quality CD, not CD-RW.  Try again.
 
As talsemgeest noted, your version of GParted isn't seeing data, and that makes me nervous.  If GParted isn't interfacing correctly with the drive then it seems like chances of success are compromised.

If you can get GPLCD to see the data blocks, that would be a good sign.  I'd still use the vista partitioner for initial resizing of ntfs partition.

Then go back in with GPLCD and make an extended partition out of the freed space so that you don't run into the 4 primary partitions brick wall, and create logical partitions inside the extended partition for Ubuntu.  Would suggest  separate "/" and "/home" partitions, then swap of course.

---

### Post by talsemgeest on 2008-02-10
Or possibly try a different partitioner?

---

