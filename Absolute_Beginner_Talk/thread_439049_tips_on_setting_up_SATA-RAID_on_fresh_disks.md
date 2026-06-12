---
title: "tips on setting up SATA-RAID on fresh disks?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by oui_buenafe on 2007-05-10
I have 2 SATA HDDs, one of which is formatted and partitioned (with LVM)--that's where the OS is--and the other is fresh, unformatted and unpartitioned.  The motherboard (ASUS P5L MX) can support RAID...so:

How can I set up a SATA-RAID (1) array?  I haven't found a how-to guide for this situation for now.  Any suggestions?

---

### Post by BHelts on 2007-05-10
you can set up an array through the BIOS, but you will lose the partition and data on the one drive.  In the BIOS you want set SATA Type as Raid.... once that has happened and you save and reboot, you will get prompted to hit something like CTL + E or CTL + I to enter the RAID Console where you can set up the mirror.

---

### Post by oui_buenafe on 2007-05-10
So does this mean that I have to re-install Ubuntu?

---

### Post by BHelts on 2007-05-11
I'm sorry for the lack of a reply.  Yes, you will have to reinstall Ubuntu.  The only other option would be to mirror the drives using software, and the right software can build the array in real time as you use the computer, as far as whether or not this type of software is available for linux, or will work with your hardware setup, i honestly don't know.

---

