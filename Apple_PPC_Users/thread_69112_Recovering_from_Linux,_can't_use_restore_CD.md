---
title: "Recovering from Linux, can't use restore CD"
date: 2005-09-25
forum: Apple PPC Users
---

### Post by Juanito on 2005-09-25
I installed Ubuntu by selecting the option of "use the entire disk". Now I can't use the restore CD given by Mac. I can only assume that's because there's no HFS partition. How can I restore it?

Thanks in advance.

---

### Post by aysiu on 2005-09-25
[QUOTE=Juanito]I installed Ubuntu by selecting the option of "use the entire disk". Now I can't use the restore CD given by Mac. I can only assume that's because there's no HFS partition. How can I restore it?

Thanks in advance.[/QUOTE] Don't you have to hold down the C key to have the computer boot from the CD-ROM drive on Macs?

---

### Post by Juanito on 2005-09-25
[QUOTE=aysiu]Don't you have to hold down the C key to have the computer boot from the CD-ROM drive on Macs?[/QUOTE]

yes :P I did that.. but when I went into the installer, and it asks me where to install Mac, there is no hard drive to select.

I should also have mentioned that Ubuntu didn't install properly (doesn't go into gnome, but commandline is ok). I also don't have internet access on it.

---

### Post by aysiu on 2005-09-25
It's too bad Apple doesn't have a [page like this](http://support.microsoft.com/default.aspx?scid=kb;en-us;314458) on its website--at least one I could find. Anyone else able to help?

---

### Post by CleverName on 2005-09-26
[QUOTE=Juanito]yes :P I did that.. but when I went into the installer, and it asks me where to install Mac, there is no hard drive to select.

I should also have mentioned that Ubuntu didn't install properly (doesn't go into gnome, but commandline is ok). I also don't have internet access on it.[/QUOTE]



What type of machine are you installing on?  It sounds like a similar problem I had italling ubuntu on a 300MHz clamshell iBook.  I could get to the command line from the log-in screen, but Gnome would crash.  Any help on getting the restore disks to work again would be appreciated.  

Short of getting the restore disks to work, I did figure out how to get ubuntu to install/Gnome to run.  If this will help:

My problem was that, due to a dead battery, the system and hardware clocks were set to some date in 1903.  If before trying to start up Gnome I reset the clocks via the command line things go just fine.

---

### Post by stuporglue on 2005-09-27
In the OSX installer, there should be a Disk Utility or Disk Manager in the menus somewhere. Note that this would be in the top menu bar NOT the installer!

You probalby don't have any HFS partitions. OSX doesn't know how to display ext3 partitions and ignores them. If you run the Disk Utility, does the HD show up? You should be able to partition the disk as desired (including 1 partition, if you only want Mac.).

---

