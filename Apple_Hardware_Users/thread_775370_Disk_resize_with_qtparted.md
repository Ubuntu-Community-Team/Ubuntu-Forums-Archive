---
title: "Disk resize with qtparted"
date: 2008-04-30
forum: Apple Hardware Users
---

### Post by dai_vernon on 2008-04-30
I'm currently booting from a PPC Ubuntu Gutsy live CD, and I have installed qtparted via sudo apt-get install qtparted and have run it.  I am trying to resize my current partition so that I can install Linux on the newly free space, but I am having some trouble. I have disabled journaling on the volume.

In Qtparted, when selecting /dev/sda (the only volume detected by the program), I am presented with 4 choices, /sda1 through 4.  sda3 appears to be the single-partition area that I am running OS X 10.4.11, as it is 149 GB.  It has 70+ GB free and I configure qtparted to shave off 38 GB to become the soon-to-be Linux partition.  When I run the program the first time, I recieve a completely blank dialogue box and the terminal outputs the following:

Error: Could not detect file system.
Error: Partition /dev/sda3 is being used.

On subsequent attempts, only the second error message appears, and the same blank dialogue box is brought up.  The partition, called Macintosh HD, is visible on the Live CD desktop and I can view and manipulate the files.  Is this the source of the error?  If so, how can I fix this?  If not, how can resolve this? 
Thanks.

Edit: Ok, I have somewhat successfully resized the disk with qtparted, and the extra space has been hacked off of Macintosh HD with no apparent damage.  However, qtparted spat an error message to the effect of "partition map has no partition map".  Back in OS X, Macintosh HD has been resized to 110 GB, but Disk Utility is not detecting an extra partition.  When analyzed, it says that Macintosh HD has 149 GB total size, 70-some GB used, and 30-some GB remaining, a total difference from the entire hard drive (149-Used-Free) equal to what I sliced off.  Where is this extra space?  How can I access it to format it for Linux?

---

### Post by dai_vernon on 2008-04-30
Never mind, everybody!  With the help of my good friend Phyphor I was able to screw with this enough to get it to go.  I reabsorbed the 38 that I cut off and just ended up using parted to resection it manually.

Hooray!

---

