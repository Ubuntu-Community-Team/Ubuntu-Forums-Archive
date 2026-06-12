---
title: "Help! Ubuntu install impossibility!"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by ess117 on 2007-07-09
I know you're all busy people, so I'll be brief:

System: Dell Dimension 8200 w/1.8 Ghz P4
Lite-On LTD163 DVD-ROM
Hitachi CDR
Western Digital EIDE drives (160 GB, 40 GB-master)

1 - Cannot boot from CD-Rom - I have booted from CDs in the past, but some point around 12 months ago, the "Boot from CD?" message disappeared from my computer.  The CD drives (1 DVD, 1 CDR) are configured with DVD as mastser and CDR as slave.  I have tried switching the jumpers to reverse this.  Both are visible and recognized correctly in the OS, and I can hear the DVD spin up during boot - I just don't get any recognition from the computer.  Going into the boot menu and selecting the CD device gives an error (F1 to retry, F2 for setup utility).  I've also tried switching the cables and putting the DVD as slave on the primary controller with the hard drive - still no dice.

2 - Cannot boot from floppy - This is unsurprising.  I think the drive is busted or otherwise nonresponsive.  I have tried a myriad of boot disks, including a standard, XP-created vanilla DOS boot disk.  I get a consistent "non-system disk I/O error" regardless of which disk I use.  This prevents me from flashing the BIOS with a newer version and it also rules out GRUB and other floppy-based boot utilities.

3 - Instlux does not work - I attempted to modify the boot with instlux, but it did nothing.  The installer runs fine and notifies that the computer files have been modified, but the boot proceeds normally (straight into XP).  When XP boots, instlux does its job and uninstalls itself.

How do I manage to solve this problem or get the computer up and running with Linux?  I've hunted around on the internet to find a solution, but I'm coming up empty.  Any solutions to this problem would be most appreciated.  Thanks!

---

### Post by AlexenderReez on 2007-07-09
firstly ,can you computer boot from usb plug?if yes then just extract ubuntu cd to a empty pendrive 1g ...then..choose boot usb first....


second..if not,you don't have any choice if can't use usb to install except use wubi 
> [https://wiki.ubuntu.com/install.exe/Prototype](https://wiki.ubuntu.com/install.exe/Prototype)

---

### Post by ramjet_1953 on 2007-07-09
Have you tried going into the BIOS setup utility and change the boot order?

Usually during boot, you press a combination of keys to enter, like CNTL+F2, or something similar. It usually tells you the key combination to enter on the POST boot screen.

Regards,
Roger 8)

---

### Post by ess117 on 2007-07-09
The boot order *should* be configured correctly.  The order is as follows:

1 - CD Reader
2 - Floppy Disk
3 - Hard Disk

I can also hit F12 to bring up a concrete menu that gives boot options selectable from a list as follows:

1 - Normal
2 - CD Rom Drive
3 - Floppy Disk
4 - Hard Disk

The Normal and Hard Disk options result in a normal boot to Windows, while the Floppy Disk and CD Drive options both give error messages.  The floppy error is described in my original post, the CD Drive error says "F1 to retry boot, F2 for setup."

There is no option to use a USB or Flash drive in the BIOS, which is a shame, since I have a 4 GB flash drive ready to accept the install image.

Thanks for the fast replies!

---

### Post by ess117 on 2007-07-09
I've tried using Wubi, and now there is another problem.

For some reason, Wubi keeps going back to the error "Step failed: Load Installer Components from CD."

Wubi correctly identifies the ISO image for 7.04 on my hard drive, so why does it need the CD?  I went ahead and burned the feisty ISO to a CD and put it in the drive for good measure, and while Wubi can check and verify the disk, it can't load the installer from it.

What up with that?

The installer also says it can't identify my Linksys Wireless-G PCI Adapter, which is the sole internet connection for the computer.  I'm currently trying to hunt down a driver I can load from a floppy.

This is the messiest install experience ever for me.

---

### Post by Calash on 2007-07-09
If you have the USB flash drive bootable and plugged in when you press F12 it should show up on the list there.

You may want to remove one of the two CD readers, leaving only 1 in the master position.  Sometimes the system tries to boot from the one the disk is not in.

You may also want to check the BIOS and make sure both CD-drives are detected there...you may have one set but it is not showing up....

---

### Post by ess117 on 2007-07-09
I've tried switching the position of the CD on startup - even putting two bootable CDs in both drives, and still no boot.  

Both drives are correctly identified in the BIOS settings, and listed under the devices on the secondary controller by model number and name.

I'll see if booting from the flash drive is possible.

---

### Post by Calash on 2007-07-09
Did you try pulling one drive and just having one on the chain?

I am wondering if one drive went bad and is knocking the other one out as well..

---

### Post by twiceasworn on 2007-07-09
When you are booting from the cd, does the drive spin as though it is trying to access the data on the cd?  If it is and it is giving an error then there could be something wrong with the disk itself.  Did you burn the disk with linux on it?  Or was it a ship it cd?

---

### Post by ageilers on 2007-07-09
Make sure jumpers are set to CS "cable select" on the drives. Have had issues with that on Dells in the past.

---

### Post by ess117 on 2007-07-09
I do not know how.

I do not know why.

I restarted the computer after a failed GRUB install whereupon booting would only give me "Error 15."  The boot CD for feisty detected, and now it's installing.  

I can only cite a gracious God with a twisted sense of humor.

Thanks again for all the feedback!

---

