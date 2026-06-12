---
title: "Help with HD..."
date: 2007-05-25
forum: Apple PPC Users
---

### Post by mrbugspray on 2007-05-25
Hey peoples,

i have a powerbook g4 that I am trying to install ubuntu feisty on. But it keeps saying, 

"**Buffer I/O error on device hda, logical block 0**"

Any help would be apprecited. Thanks in advance. :)

---

### Post by stmiller on 2007-05-26
Hey we can help. What is the exact model of your powerbook? 
(See [www.apple-history.com](www.apple-history.com) )

Some people have had to install with the alternative PPC Feisty CD instead of the live CD. This goes directly to the installer (no live desktop).

---

### Post by mrbugspray on 2007-05-26
> **stmiller said:**
> Hey we can help. What is the exact model of your powerbook? 
(See [www.apple-history.com](www.apple-history.com) )

Some people have had to install with the alternative PPC Feisty CD instead of the live CD. This goes directly to the installer (no live desktop).

It's a 1.33 ghz G4 with 512 mb of ram and an 80gb hard drive.

---

### Post by tcrroadie on 2007-05-26
Due you have a free partition set up for Ubuntu all ready?  I set my ibook g4 to dual boot OS X and Ubuntu Feisty  by first reinstalling OS X and creating a second partion for Ubuntu during reinstallation, using the Disk Utility on the OS X installation disk.  The following instructions is how I set my G4 ibook up for Ubuntu Feisty.  I also had no problems installing Feisty on my ibook using the live cd. 

1. Insert the OSX Software Install CD or DVD.
2. Restart your computer.
3. Hold the "C" key until you have booted from the OSX Software Install
4. Select the Install menu at the top of the screen.
5. Select 'Open Disk Utility'.
6. Select Mac HD (or the name of the drive that contains OSX).
7. Select the Partition tab.
8. Under the Volume Scheme menu, choose "2 Partitions," one for OS X and
one for Ubuntu.
9. Select the first (top) partition, "Untitled". It should be gray.
10. Use the Format menu to the right and choose "Free Space." This will be
your Ubuntu partition.
11. Move the slider at the bottom of the partition to increase or decrease its
size or, alternatively, enter your preferred size in the Size text box to the
right.
12. Select the second partition. This should be your MacOS X partition.
Keep it OSX (HFS Extended), and resize as desired.
13. Name this partition "OS X" or whatever you like.
14. Click the "Partition" button at the bottom of the screen and then again
at the prompt.
15. Quit Disk Utility.
16. Resume your OS X install.

Good luck.  Ubuntu Feisty is actually very good on the PPC ibook and Powerbooks.  I have everything I desire working (wireless, media, (mp3, avi, mp3g, wmv, quicktime) except of course Flash.  It is very nice.  I actually prefer Gnome over Aqua.  Everything works great.   

Let us know if you need more help.

A screenshot of my Feisty on my ibook to help keep you going.

---

