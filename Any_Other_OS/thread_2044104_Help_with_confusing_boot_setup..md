---
title: "Help with confusing boot setup."
date: 2012-08-18
forum: Any Other OS
---

### Post by Dr. Nick on 2012-08-18
I am about to reinstall my computer and I would like help setting up my boot loader. I want to have XBMCbuntu and Windows 7 installed on a single hard drive (separate partitions). I will primarily use XBMCbuntu as a HTPC so I want it to boot as fast as possible, However I want Win 7 around for other things. 

I would like XBMCbuntu to load automatically (not even seeing Grub) and Windows 7 to only boot when a certain USB stick is plugged in. I am fluent with both operating systems and computer BIOS just cant think of how to accomplish this. I can set USB to a higher boot priority in the BIOS so I will get recognized before Grub even starts. Basically I guess I just need a way to install just the bootloader for windows on the the USB drive and edit it to point to the correct partition of the internal drive.

Any tips?

---

### Post by papibe on 2012-08-18
Hi Dr. Nick.

This is what I would do:
[LIST=1]
[*]Use the Ubuntu installation media as a Live CD/USB.
[*]Partition the disk using gparted.
[*]Boot into your Windows installation and install it on the partition you designed.
[*]Test you can boot normally on Windows.
[*]Boot into the XBMCbuntu installation media and install XBMCbuntu on the other partition you created. Install grub as part of the installation. In case you can't install it, you will fix it on step #7.
[*]Test that you can boot your machine into the grub menu and boot correctly both OSes. If this is not working you can fix it on the next step.
[*]Boot again into the Ubuntu media as Live, and use [this]("https://help.ubuntu.com/community/Boot-Repair") steps, using 'Boot Repair' to set your default OS, and grub menu time (to zero).
[/LIST]
Let us know how it goes.
Regards.

---

### Post by Dr. Nick on 2012-08-18
That will work to get to get both installed with a fast boot into XBMCbuntu like I want, but what would I have to do to get into Win 7 with that setup? Would I have to change the menu time each time? The more I look at it I may just set it up the traditional way with XBMCbuntu the default OS and just set a short timer, A 5 second boot delay wont kill me and seems much more simple then messing with the bootloaders.

---

### Post by papibe on 2012-08-18
> **Dr. Nick said:**
> Would I have to change the menu time each time?
Not at all.

You would have to just hold the 'shift key' during boot to get to the grub menu.

Regards.

---

### Post by Dr. Nick on 2012-08-18
> **papibe said:**
> Not at all.

You would have to just hold the 'shift key' during boot to get to the grub menu.

Regards.

Oh cool, I did not know shift showed the menu. Thanks I will get started on this tomorrow and let you know how it goes.

---

### Post by oldfred on 2012-08-18
I think some have had issues with it set to 0 as then you have no time for shift although it still should work. I might try 1 sec just to be safe.

You can just install a grub to the flash drive and then create your own grub.cfg to boot anything you want. I use grub on flash drives to loopmount ISO and also add boot entries to some of my installs on the hard drives just as a backup.

---

