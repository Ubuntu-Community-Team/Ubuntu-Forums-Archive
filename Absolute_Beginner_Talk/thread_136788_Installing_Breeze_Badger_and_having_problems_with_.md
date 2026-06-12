---
title: "Installing Breeze Badger and having problems with partitioner"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by quari on 2006-02-26
Hi there - I'm completely new to ubuntu and pretty new to linux so be gentle!

I have a 5.10 CD and trying to install on a crummy Compaq ARMADA E500 laptop so I can use it as an extra machine on the network for email and web surfing while my big machine does other work.  

The laptop previously had win98SE installed (yuck, I know!) and when I boot from the ubuntu cd it all seems to go fine until it gets to the partitioner step.  Then it gets to 52% and stops.  There are no partitioner options at this point, it just appears to be checking out the HDD.  My more linux savvy friend checked it hadnt crashed by going into the console but thats about all I know.  I left it for an hour or so and still no movement.

I know I have a slow computer here and a crappy HDD but its small so it shouldnt take that long.

Any ideas?  

Thanks!

Quari

---

### Post by pestilence4hr on 2006-02-26
A few things you could try.  If you back out of any of the installation steps, it should dump you to a list of tasks.  Try jumping directly to "Partition disks", and wipe the disk.

OR

Go to the console that your friend told you how to get to.  Run cfdisk, and wipe the partitions that are on there.  Then try the install again.

OR

Use a live cd, and run cfdisk from there.

---

### Post by wiljohnson on 2006-02-26
would guess you are short on 
RAM or HDD space -- just tried to install 5.1 on an AMD 466 laptop which had 64M 
RAM and 6 G HDD.   Could not complete install.  
Have been running 5.1 on a 1 ghz celeron with 128M RAM and 40 G HDD with no install problems for about one month now.

---

### Post by quari on 2006-02-26
Thanks for both suggestions - I will try to get it working using cfdisk as suggested and if not might look for a less intensive solution - is xubuntu any better for old slow machines?  I really don't want to use it for much more than the odd google search etc.

---

