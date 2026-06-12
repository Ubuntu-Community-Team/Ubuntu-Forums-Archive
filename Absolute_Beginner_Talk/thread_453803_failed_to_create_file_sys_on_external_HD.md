---
title: "failed to create file sys on external HD"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by yamswirl on 2007-05-24
I've been looking through the forum and online to work this out and I'm just not getting it.

I have a SimpleTech 400gb external hard drive that I really want to use.  I've tried to install 6.06, using all the space.  It gets to 15% and says, "failed to create file system." 

As far as I can tell the ntfs is gone and linux has overwritten all the old system.  My laptop recognized the hd when I plug it in.  The only folder showing up is "lost and found."  

At one point messing around with it it also said there was "no root system found."

So, how do I go about creating a file system and/or a root system so I can install 6.06 and write to this hd?

I'm really still learning linux so step by step instruction are great!  Like you're talking a 5 year old through it.  But not one of those wicked smart 5 year olds.  ;)

Side note, I've tried to install Feisty on the laptop and external hd and it always gets to about 5% and hangs then doesn't install.  So I've put that aside for now. 

Thanks for any incoming help.

---

### Post by dstew on 2007-05-25
See this post:[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)

The problem is that the Ubuntu Live CD may "mount" the hard drive onto its filesystem. The partitioner and formatter cannot work on a mounted drive.

You can also use the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") to partition and format the external drive, before you try to install Ubuntu.

---

### Post by yamswirl on 2007-05-25
Thanks!  I'll take a look at it and see if it helps.

---

### Post by Bartender on 2007-05-25
Use GParted LiveCD to delete all partitions, then click on the map of the blank drive, set it to "unformatted", and Apply.  Not "unallocated".  I tried that the other day.   Xubuntu wouldn't install to the drive until I had GPLCD unformat the drive.

---

### Post by yamswirl on 2007-05-29
\\:D/  Thanks!  It's a working hard drive again!  Yay!

---

