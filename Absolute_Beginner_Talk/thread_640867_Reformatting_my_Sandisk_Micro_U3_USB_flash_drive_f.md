---
title: "Reformatting my Sandisk Micro U3 USB flash drive from terminal?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2007-12-14
I need my flash to work in a Windows and Linux machine. 

Here's how I destroyed everything. I was reinstalling Windows on my brothers PC and I accidently formatted my flash drive from the blue menu where you choose where to install Windows.

You know, press L to format, etc, etc.


So any ideas on how to fix it again? I don't care if I don't have U3 anymore. All I want is to have my portable 2Gb back! 

PS. Gparted doesn't work on my PC, it keeps scanning forever into oblivion.

---

### Post by andrewc6l on 2007-12-14
I did something similar to this. I did a newfs on the drive. I believe I had to uninstall U3 before I could do anything else. You might want to try that - the uninstaller is at:
[http://www.sandisk.com/Retail/Default.aspx?CatID=1415](http://www.sandisk.com/Retail/Default.aspx?CatID=1415)
(windows only).

After that, you should be able to mkfs -tntfs and build a new filesystem there. If you don't put a partition table on it but instead just mkfs the entire device, you'll get a little more storage.

    Andrew

---

