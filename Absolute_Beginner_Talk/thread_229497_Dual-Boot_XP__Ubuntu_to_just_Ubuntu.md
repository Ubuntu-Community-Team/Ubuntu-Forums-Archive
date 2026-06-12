---
title: "Dual-Boot XP / Ubuntu to just Ubuntu"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by adeax on 2006-08-04
I am thinking about setting up Ubuntu on my media PC to run MythTV.  Right now it is running off of Windows.  I have a new hard drive that I am going to be using.  My thought process was that I would install the new hard drive, install Ubuntu there, and have the computer be in a dual-boot configuration.

I'd like to keep it like this until I can get MythTV working reliably and then take out the original hard drive with Windows installed on it and just leave the Ubuntu drive in and get rid of the dual-boot configuration.

Is this possible?  What would be the best process?  Thanks in advance.

---

### Post by zxee on 2006-08-04
Are these drives IDE? You generally can't go removing a slave or master drive without the computer's bios having a fit. 
You are going to have at least two partitions anyway so plan your partition space for your needs, considering the idea to totally remove windows, and when/if that day comes you can simply delete the window's partition.
If you're talking sata then it's a different story-you can probably do what you orginally wanted under sata-however changes to fstab may be required.

---

### Post by Nordkraft on 2006-08-04
Another possibility, which might seem a bit troublesome though, but could rid you of potential problems with pulling out a drive in a dual boot setup:

Unplug the win-drive. Install the new hd. Set up Ubuntu on the new hd with the win-drive still unplugged. Once Ubuntu is set up, plug in the win-drive and now you have two seperately working systems (sort of hardware dual boot). For this to be convenient for you, your comp. should have a "press F8 for boot configuration"-type of deal, where you can easily choose from which hd you wish to boot, as you boot up but before any OS is loaded. 

As I said, this might seem a little troublesome, but it sure works:)

---

### Post by aysiu on 2006-08-04
Instead of removing the Master drive (unless you need it for something else--another computer maybe), just delete the Windows installation and make it Ext3. Then Ubuntu can use it as more space. If Ubuntu's Grub is installed to the MBR (which is the default behavior during installation), then getting rid of XP is as simple as deleting it and then getting rid of its entry in the /boot/grub/menu.lst file.

---

