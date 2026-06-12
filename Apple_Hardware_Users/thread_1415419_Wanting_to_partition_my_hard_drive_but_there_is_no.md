---
title: "Wanting to partition my hard drive but there is no free space available"
date: 2010-02-24
forum: Apple Hardware Users
---

### Post by c0bracommander on 2010-02-24
I just installed a new hard drive with OS X on my iMac G5 PowerPC. The drive size is 1TB. OS X Leopard is currently only using about 80 gigs of that space.

For some reason, at the disk preparation from my live PowerPC Ubuntu install, the entire bar is green with only 8kb of (white) free space.

I want to partition the computer to add Ubuntu to it, but I don't want to risk partitioning my hard drive and losing any data affiliated with the current o/s installed on it (OS X Leopard).

What is the best way to go about doing this? A manual partition? I'm afraid I've never done this before, so I'm not sure how to go about this.

---

### Post by Dr Droid on 2010-02-24
THIS IS MY FIRST POST EVER 

But in response to your question, have you tried using GParted to resize the partition or any other package besides the live PowePC Ubuntu install?

It seems that the original install of OSX had consumed the entire size of the drive as its root partition. If you want to dual boot you need to resize the first partition and the create and format (ext3) a separate partition for ubuntu...

This is my understanding having never really dealt with OSX installations

---

### Post by linuxopjemac on 2010-02-25
[http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=17](http://mac.linux.be/phpBB3/viewtopic.php?f=14&t=17)

---

### Post by wheeeler on 2010-02-25
This is a well-documented task on several forums, but here goes:
 
Mac OS X occupies the entire disk by default, and using GParted or any other partition manager to create a new partition table will wipe out your current partition table and all data on the disk.  Leopard ships with Boot Camp Assistant, and is a great way to adjust your Mac OS X partition without losing your data.
 
Use Boot Camp Assistant to resize your Mac OS X partition and create a FAT partition at the end of the drive that you will convert to free space later on.  Quit the assistant when it asks you to insert your Windows install disc.  Now pop in your Ubuntu CD and reboot while holding 'C'
 
Jump through the usual hoops (language, time zone, etc), and when you are asked how to partition your disk, opt for manual configuration.
 
Click your Windows (FAT) partition and delete it (I'm at work, so I can't give you a precise step-by-step on this).
 
You now have free space at the end of your drive.  Double-click on it to change it to something useful, like a new ext3 partition.  Don't forget to save some of that free space for your swap partition!
 
Hope this helps.

---

### Post by kmag on 2010-02-25
I had to register to write this.  I have heard many explanations how to do this that make this WAY more difficult than it is.

Use Apple's disk utility to reduce the size of your mac partition.  Reduce it by the amount of space you want Ubuntu to use.  Leave this free space.

Quit disk utility.

Install Ubuntu

There will be a new option available when given partition choices since there is a reasonable amount of free space available. 

Click on "Use largest contiguous free space"

The install does all the work for you, including the partitioning.

Happy Ubuntu

---

