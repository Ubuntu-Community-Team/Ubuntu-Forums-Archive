---
title: "Ubuntu for use on a power mac g4"
date: 2014-01-28
forum: Apple Hardware Users
---

### Post by Peter_Holmes on 2014-01-28
Hi Everyone,
                i am new to Ubuntu as i have been using windows 8. I would like to install Ubuntu on an Apple Power Mac G4 for a neighbor who cannot upgrade his comp anymore, but have got no idea how to do this and what i would have to adjust to make it work. I have increased the ram to the max but that is it. Any help would be appreciated.
Thank You
Peter

---

### Post by joey8 on 2014-01-28
This may or may not help I have little to no experience with installing on macs. But there is a wiki dedicated to it [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) this will get you started at least, others may be of more assistance. Link to powerPC OS versions [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by tgalati4 on 2014-01-28
Check to see if the CD burner can handle 700 MB disks.  Earlier macs had drives that could handle 650 MB disks, so burning an installation ISO on a 700 MB disk would result in an installation that failed at 90% with no obvious reason.  I don't think those macs can boot from USB.  They can boot from an external firewire drive using target mode, so you may want to take out the old Mac OSX drive and put it in a firewire exclosure and put in a new/old drive for Ubuntu.

That will give you dual-boot without risking the data on the original drive by trying to repartition it.

---

### Post by Peter_Holmes on 2014-01-28
Thanks for the advice i will check it out in the morning. Could i download ubuntu onto a spare HDD and boot it from that over USB.
Pete

---

### Post by Lars Noodén on 2014-01-28
Lubuntu has a PPC version.  You might look into it.  That should fit on a CD-R or CD-RW.

You might be able to boot from USB.  The notes I have are to start OpenFirmware (cmd+opt+o+f) and then boot the appropriate USB device:

```

boot usb1/disk@1:2,\\yaboot

```

It might be usb0.

---

