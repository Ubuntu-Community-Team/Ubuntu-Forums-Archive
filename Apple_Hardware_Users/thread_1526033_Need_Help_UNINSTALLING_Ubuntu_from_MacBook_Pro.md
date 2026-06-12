---
title: "Need Help UNINSTALLING Ubuntu from MacBook Pro"
date: 2010-07-07
forum: Apple Hardware Users
---

### Post by BenElroyHyams on 2010-07-07
Hello.

Today I installed Ubuntu on my MacBook Pro, and have decided I'd like to remove it. Here's what I did to install:

1.) Created Ubuntu CD using Disk Utility

2.) Created 32 GB partition using Boot Camp

3.) Installed on said partition.

The problem now is Im not sure how to go about uninstalling. Whenever I turn on my computer I am greeted by this screen: [IMG]http://tinypic.com/r/zkie53/3[/IMG] [http://tinypic.com/r/zkie53/3](http://tinypic.com/r/zkie53/3) (I can still use OS X by holding down option before that appears)

And my disk utility now looks like this: [IMG]http://tinypic.com/r/2lkywsm/3[/IMG]  [http://tinypic.com/r/2lkywsm/3](http://tinypic.com/r/2lkywsm/3)

Any help on what to do to get my computer back to what it was like before I tried this would be very much appreciated!

---

### Post by kanikilu on 2010-07-07
You didn't use rEFIt to dual-boot?

It's been a while since I tried Ubuntu on my Mac, but I followed the directions on this page:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:%20Mac%20OSX%20and%20Ubuntu)

And removing it was as simple as deleting a couple folders from the Mac OS X "side":

[http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)

And then using the Mac OS X install disc to delete the unwanted partition and expand the main partition back to the full disk size...

I'd probably just end up doing a reinstall of OS X, but don't do that yet in case someone here is more familiar with Mac than I, and knows if there is a way to restore the original bootloader/MBR.

---

### Post by JohnAtilano on 2010-07-07
Here is how I normally uninstall.  This is the nuclear option but it works:

1.  Remove rEFIt as outlined in the instructions above.
2.  Make a clone of your hard drive using SuperDuper! or CarbonCopyCloner.
3.  Boot from the clone.
4.  Use Disk Utility to to erase and repartition your internal HD.  (one partition, GUID partition table if on an Intel Mac).
5.  Use SuperDuper or CarbonCopyCloner to clone the backup to the Internal drive.
6.  Select your internal drive as your startup disk in System Preferences --> StartUp Disk.
7.  Reboot.

---

### Post by gaboguy7 on 2010-12-28
I have a macbook pro 6,2 and what I did was:
1: erased rEFIt by deleting the efi folder in my HD then deleting the rEFIt blesser in Library>Startupitems folder (which is in the Macintosh HD).
2: open disk utility
    a)erase the linux partitions (i had two, the main and the swap) by clicking on them in the side bar and going to the erase tab. in the format drop-down menu, select "ms-dos" and click erase (just erase, not any of the others).
    b) click on the main disk (usually located above Macintosh HD), go to the partitions tab, select the two linux partitions you want to erase (in the volume scheme which is the visual representation of what your disk and it's partitions look like), and click the minus button underneath the volume scheme. in the dialogue box that appears, click remove.

that should do it.

---

