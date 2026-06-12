---
title: "External 1T Harddrive won't mount"
date: 2013-06-03
forum: Any Other OS
---

### Post by Keyana on 2013-06-03
Hello.

My external 1T drive produced an error on my Windows Vista and stopped being accessible. Other computers could access it for a while and then it wasn't accessible to anyone. It wouldn't mount on Gentoo, and it won't mount on my Mint desktop although it does show up as a drive, it just won't mount.

So I searched the forums and found a post about a similar situation, and the first piece of instruction was the following code and to post the output.

 sudo lshw -C disk

 *-disk
       description: SCSI Disk
       product: 41AS
       vendor: ST315003
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
       version: 3004
       serial: 00A123457DBB
       size: 1397GiB (1500GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=6 guid=466e3284-ac6a-11e0-a04e-001ff33ea433 sectorsize=512

Please help a Linux n00b get back her hard drive of squee.

---

### Post by Perfect Storm on 2013-06-04
**Thread moved to Other OS/Distro Support.**

---

### Post by mips on 2013-06-04
First things first, did you remove it from the USB enclosure and connect it to your PC via a SATA interface?

---

### Post by Keyana on 2013-06-05
Sort of yes. I took it out of the case and put it into a brand new case because I couldn't get my hands on a SATA interface. On my windows laptop I also downloaded a partition repair program and scanned it for repare (unfortunately I can't remember the name of it), and the drive and came out with it being an unformated drive. But then again, the other day an hour or so after I posted this, the drive appeared to work for about five minutes just plugged in to the Mint desktop without doing anything. So I have no idea if it's just stuffed or if my data can be rescued.

---

### Post by mips on 2013-06-06
> **Keyana said:**
> **Sort of yes**. I took it out of the case and put it into a brand new case because I couldn't get my hands on a SATA interface.

plugged in to the Mint desktop without doing anything.

So that's a no then.

Open up your desktop and connect the drive to the motherboard via a sata cable. The power & sata connectors on a desktop are the same as on a laptop and they fit without any funny interfaces etc.

Once you have done that we can run some command to gather info.

---

### Post by Keyana on 2013-06-06
Unfortunately, my desktop is old. Like, doesn't have any SATA connector cables old. I've only got IDE cables. The only adapters I could find to possibly buy were SATA-to-USB not SATA to IDE, I don't even know if this motherboard takes SATA, granted, my hardware tech knowledge is about as old as this desktop... Lol.

Does this essentially mean I'm probably going to have to save up and go to a technician?

---

### Post by mips on 2013-06-06
> **Keyana said:**
> Unfortunately, my desktop is old. Like, doesn't have any SATA connector cables old. I've only got IDE cables. The only adapters I could find to possibly buy were SATA-to-USB not SATA to IDE, I don't even know if this motherboard takes SATA, granted, my hardware tech knowledge is about as old as this desktop... Lol.

Does this essentially mean I'm probably going to have to save up and go to a technician?

What motherboard do you have?

---

### Post by oldfred on 2013-06-06
You seem to be getting some info that drive may be gpt partitioned? That would be a bit unusual with Vista, as only 64 bit Vista can even read gpt partitioned drives. Gpt partitioning is the new partition scheme used with new computers that boot with UEFI or very large drives over 2TB. Most drives were MBR(msdos) partitioned.

What format was partition(s) on drive? Often external drives get disconnected incorrectly and need chkdsk if NTFS or fsck if a Linux ext2, ext3, or ext4 format.

Post this, if drive can be seen:
 sudo parted /dev/sdb unit s print

Otherwise you may want to see if testdisk can see drive:
      
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")

---

