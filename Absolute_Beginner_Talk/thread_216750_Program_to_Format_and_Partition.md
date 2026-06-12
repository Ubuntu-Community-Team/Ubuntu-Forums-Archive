---
title: "Program to Format and Partition"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by forumposters on 2006-07-16
I currently have Windows 98 on a machine, but I no longer want to use that.  What can I use to erase everything clean and then partition the harddrive for Ubuntu?

---

### Post by [S|G] on 2006-07-16
Just use the installer on ubuntu CD. You will have an option to do that.

---

### Post by molly_001 on 2006-07-16
Before doing any of the below, download and burn the .iso image of GParted.

If you possess the install CD for Windows 98, you can put that in and go up to the part where it will format the drive into a single ntfs partition.

Let it partition the entire drive into one big ntfs partition -- use the slow method for format (not the Quick Format or whatever it's called).

Then just abort the installation after the formating is done.

Next, pop in the GParted CD.  You have a number of partitioning options available to you.  The smartest of these is perhaps the plan involving linux ext3 (for Ubuntu), followed by a separate /home partition (for your docs), and then a small Swap partition (necessary).

You can find more info on this here:
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

(Ignore the parts from that web page regarding ntfs.)

---

### Post by Loki1989 on 2006-07-16
when you pick to install pick manual and delete the partition for win98 its simple when you look at it it's gparted that the partition program on the CD

---

### Post by forumposters on 2006-07-16
I've booted from the ubuntu CD and it gives me an option to simply resize the partition that Windows 98 is using and install it using only 2.4 GBs.  What's wrong with just doing that?

---

### Post by [S|G] on 2006-07-16
2.4GB might be a bit too small for a normal, non-server installation. Plus if you will be keeping your files in Ubuntu's disk you will also need extra space for them.

---

