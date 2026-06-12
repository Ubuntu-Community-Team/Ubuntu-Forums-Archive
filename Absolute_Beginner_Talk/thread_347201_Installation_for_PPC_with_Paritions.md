---
title: "Installation for PPC with Paritions"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by brontosaurus on 2007-01-26
Hello everyone,
I have an iBook G4, and I want to install Ubuntu on a partition.  I have the normal Apple partition scheme with a free 22 Gig HFS+ partition (in addition to two other usable partitions for OSX and media files, respectively), and I'd like to put Ubuntu on this partition.  How can I get this to work with the partition manager, considering that I also need a swap partition and I really don't want to wipe my HD?

The only choice that I see is to delete the partition, but I don't want to screw anything up, so I'd like to know what I can do from there and whether this would work at all.

Thanks for your help!

---

### Post by Pobega on 2007-01-26
When you get to the part of the LiveCD that asks you how you would like to partition, select "Manually edit the partition tables". Then just delete the 22 GB partition, and reformat it as ext3 (Or you can just right click -> Reformat, if memory servers me right). You may also want to take 2 GB off of that for a Swap partition, so you would have a 20GB root ( / ) partition. 

Then when you click next the installer will ask you what you want to do with each partition. Make sure you set the 2GB as swap and the 20GB as Root, and **do not reformat** (meaning **untick the box**) your OSX/Media partitions; This will leave those untouched, and the installation will continue on the two Ubuntu partitions (Swap and Root)

---

### Post by rccharles on 2007-01-27
> **brontosaurus said:**
> Hello everyone,
I have an iBook G4, and I want to install Ubuntu on a partition.  I have the normal Apple partition scheme with a free 22 Gig HFS+ partition (in addition to two other usable partitions for OSX and media files, respectively), and I'd like to put Ubuntu on this partition.  How can I get this to work with the partition manager, considering that I also need a swap partition and I really don't want to wipe my HD?



MacOS X has lots of hidden partitions.  Just leave them alone.

You could use the MacOS partition tool ( disk utility ) to delete the 22gig partition.  This will live the space free on the harddrive. When you install Ubuntu, you can tell the installer to use the largest free space and the installer will do the rest.

Once you have installed Ubuntu and want to boot to Ubuntu, you should hold down the option key when you power up your iBook.  This will bring up the MacOX boot loader.   Use the mouse to select the Linux partition.

Robert

---

