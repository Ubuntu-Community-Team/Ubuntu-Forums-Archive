---
title: "Dual Boot OSX 14.04.1 on MacPro Retina 11,2 - Unsure of instructions"
date: 2014-10-18
forum: Apple Hardware Users
---

### Post by spmcc123 on 2014-10-18
New to this. Following instructions [here]("https://help.ubuntu.com/community/MacBookPro11-1/Saucy"): I have bootable USB with Ubuntu 14.04.1 (the NON-MAC 64 BIT, per instructions).  I created a 35GB partition for Ubuntu on the MacPro (running OSX 10.9 (Maverick)) using Disk Utility.   I have been able to boot into Ubuntu by holding down Option key on restart.   Following instructions, I have selected "Try Ubuntu Without Installing" and, once the Ubuntu desktop is up, I clicked the "Install Ubuntu" icon... so far so good.

However, in the first dialogue box I don't have the option to install "Alongside with MacOSX", as I was led to believe I would have...  Instead I see:

[[IMG]http://i.imgur.com/QKkicEU.jpg[/IMG]]("http://imgur.com/QKkicEU")

If I pick "Something Else" I get this screen:

[[IMG]http://i.imgur.com/AJMUmuv.jpg[/IMG]]("http://imgur.com/AJMUmuv")

and have no idea what to select in order not to wipe out OSX (which I need for various apps). I kind of guess it would be sda4 hfs+, since that is about the size I created in Disk Utility, but I really have no idea how to proceed and a search of Ubuntu documentation and this board hasn't turned up a solution....     I don't know what to do with "New Partition Table" since my installation instructions (again, [here]("https://help.ubuntu.com/community/MacBookPro11-1/Saucy")) state:* "Resizing MacOS partition during Ubuntu installation may damage your MacOS.*" and the warning box would indicate I don't want to do this...

[IMG]http://i.imgur.com/mP4GZLc.jpg[/IMG]

any advise on how to bring up the 35G partition I set up to host Ubuntu?  I am told by the instructions that I should "....NOT need rEFIt or rEFInd or boot-repair after installation..."

---

### Post by sotiris2 on 2014-10-19
I think the problem is that "Install alongside MacOsX" probably requires unallocated space on the disk and won't touch any existing partitions. On your disk since you created a HFS partition (which ubuntu can't use to install itself) on the space you made from resizing, the installer can't offer you an automatic side by side install.  I suggest you boot OSX and delete the empty partition, thus leaving unallocated space on disk. You 'll probably get the "Install alongside osx" option then. 

In any case do follow the tutorial throughly and if you don't understand something it says do post before implementing it. In no case should you create a new partition table since that will WIPE THE WHOLE DISK.

---

### Post by spmcc123 on 2014-10-19
Thanks so much for the advice.  Yes, I am moving through the installation process cautiously because of the potential consequences and will post back here for other newcomers....  

Following the Saucy Salamander instructions, the very first point (in fact, point 0.) is:

*"0.   If you want to keep the MacOS, boot into MacOS and use its Disk Utility  to resize the MacOS partition to open up space for Ubuntu.  (I would  open up at least 25GB, with ~20GB for / and about 4-8 GB for swap.)   Resizing MacOS partition during Ubuntu installation may damage your  MacOS*."....  I am concerned that trying to create the partition during installation I might..."damage [my] MacOS...."

I tried going straight to "Install Ubuntu" (instead of "Try Ubuntu"), but the same set of screens come up.  

To check out your hypothesis, I removed the second partition and booted from the Ubuntu USB and the same set of screens came up.  No option to "Install alongside...", just "Replace..." and "Something else"

As it stands, I assume that I will eventually need to partition in advance using Disk Utility, then boot from the USB and select the sda4 (hfs+) partition and install there, but I will wait for a while to see if you  or any other experienced user can make sense of the situation...    Happy to use a different Ubuntu build, if that might come with a different installation procedure.  I was last on Pangolin...

---

### Post by Kale_Freemon on 2014-10-20
Well, you don't want sda4 to be hfs+. That's a Mac filesystem that Ubuntu cannot use to install itself on, as suggested in the first reply. If that is indeed the parition you want to install Ubuntu onto, you can reformat it in the installer by selecting it and clicking change. Choose Ext4 as the filesystem and then "/" (without quotes) as the mount point. Just, do not touch the sda2 partition. That is labeled as Mac OS X. Again, do NOT touch sda2!

---

### Post by Elfy on 2014-10-20
If you're not sure which partition is which while in the the Ubuntu installer - stop.

Boot into the existing OS and deal with the partitions there - I would suggest that rather than creating a partition (which will then be of no use) to just leave free space.

Then you can boot the installer and it will see the free space.

---

### Post by spmcc123 on 2014-10-20
Got it.  My mistake was to create a partition for Ubuntu in Disc Utility rather than freeing up space for Ubuntu to create its own. In fact, I had not known until these replies that one could shrink a partition and merely leave the remaining space as "free" (rather than immediately assigning it to a new partition).  Thanks for assistance.

---

