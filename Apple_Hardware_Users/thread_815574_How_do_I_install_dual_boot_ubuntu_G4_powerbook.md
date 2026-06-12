---
title: "How do I install dual boot ubuntu? G4 powerbook"
date: 2008-06-01
forum: Apple Hardware Users
---

### Post by ruialexbarbosa on 2008-06-01
Hi,

12", 60gb, 512ram powerbook, with 10.4 OSX. I want to install latest version of live cd ubuntu.

How do I setup partitions? I would like to keep OSX with about 20gb, create a 20gb shared partition, and have another 20gb for ubuntu. Does this sound ok? How do I do it?

Thanks for any help.

---

### Post by mfox on 2008-06-01
This is very similar to the way I set up my PowerBook G4 15" Al.  I have an 80gb disk in it, my PB is running with Tiger and I wanted a dual boot.  First step is to back up your Mac, just in case you do something wrong.  Next, free up some HD space for Ubuntu.  I did this using a utility called Drive Genius, but you can do it in Disk Utility as well.  What you want to do is shrink your Mac partition, leaving the extra space as free space (not formatted as MacOS X extended).  You can do this by selecting the drive in Disk Utility and then the Partition tab.  When you've shrunk the Mac partition, note its size and that of your free space; helpful reassurance later when Ubuntu suggests the partitioning during the installation.

Download the Ubuntu PPC Live Installer and burn it to a CD (you can get it [here]("http://cdimage.ubuntu.com/ports/daily-live/current/"), assuming you want 8.04.  (That's what I put on, but note that if you are dependent on Mac-on-Linux for running Mac programs on Ubuntu, you might want to go with 7.10 instead.) I went with Hardy and was able to do it with the Live CD; I didn't need the alternative.  Your architecture is almost the same, so I assume that you can use the Live CD as well.  I allowed the installer to select the partitioning scheme; it will use the largest free space you provide as a default.  The installation should be pretty straightforward and when it's done, you'll have a dual boot system.  Good luck!

---

