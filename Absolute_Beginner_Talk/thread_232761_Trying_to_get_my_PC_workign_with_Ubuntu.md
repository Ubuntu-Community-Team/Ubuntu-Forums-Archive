---
title: "Trying to get my PC workign with Ubuntu"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by terry.turner on 2006-08-09
I am new to Ubuntu and Linux. having defected from Windows. Somehow my CDs got corrupted and I can´t afford new ones.

AFter several insatllations of the Alternate CD with the EOm install I reinstalled with a text install.  However most of the problems I was experincign were still there.

I have a slave hard drive which contains my data files, a floppy drive and CD reader/writer.

The first problem is that I can not read anything on my floppies.

The floppy is lited in the "My Computer" in "places" but when I try to read any files on floppies it tells me that it canñt "mount" it, and ther is some problem with not knowing the filesystem.  How do I fix that please?

My slave hard drive is listed twice in "places" but I can´t "mount" that either,(Once in its own right, and also as it´s name of ´saved files´. Again i can´t "mount" it or read the data.

I can´t connect to the internet.  I have a network ethernet card which is connected via cable to a router, which is then connected to ADSL here in Spain.  What can I do to get connected? Under Windows it did it all for me.

Finally, I expect that I need to install my printers.  I have a Samsung ML Izzie laser printer and an Epsom Stylus CX3200 all in one.  I have the disc for the Samsung but can´t find the disk for the Epsopm (I may have to download a driver I expect).

Any advice is easy to follow steps would be appreciated.:-({|=

---

### Post by xpod on 2006-08-09
I believe you need to "mount" such things as floppys and hds.
im new myself so someone with more experience will come along but dont panic,
These are relatively simple procedures to carry out.

As for your printers...my old epson stylus colour 800 showed up ok without having to do much other than add new printer in the printer folder.

Im new to pc`s full stop and had only been with xp/m.e for a few months so if i can get by im sure with the right direction you`ll manage just fine.

Theres good threads out there about mounting but it`s sometimes better if your walked through those initial attempts....

---

### Post by steve.horsley on 2006-08-09
Make sure the floppy driver is installed. Try the command > lsmod | grep floppy (that's a vertical bar, not a letter L) and see if a floppy module is listed. If not, use this command to install the floppy driver:
> sudo modprobe floppy


To mount the floppy, try these two commands:
> sudo mkdir /media/floppy
sudo mount -t vfat /dev/fd0 /media/floppy and see how it goes.

Read this web page about mounting windows disks:
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

Networking: Can you post the results of the command **ifconfig** please.

---

### Post by 3rdalbum on 2006-08-09
> **terry.turner said:**
> My slave hard drive is listed twice in "places" but I can´t "mount" that either,(Once in its own right, and also as it´s name of ´saved files´. Again i can´t "mount" it or read the data.

I can´t connect to the internet.  I have a network ethernet card which is connected via cable to a router, which is then connected to ADSL here in Spain.  What can I do to get connected? Under Windows it did it all for me.

If your hard drive is listed in the Places menu, surely it's already mounted. What exactly happens when you choose it? Does it tell you that you don't have the correct permissions to read it? (a common thing when using NTFS-formatted drives)

The technology that lets Windows detect your broadband router automatically is called DHCP. I'm assuming when you installed Ubuntu that you skipped the DHCP detection step.

Go to "System > Administration > Networking". Click "Ethernet Connection" then the Properties button. Change the popup menu there to "DHCP". Close the Properties window, then click the Activate button if available.

When you close the control panel, you should have Internet access.

---

