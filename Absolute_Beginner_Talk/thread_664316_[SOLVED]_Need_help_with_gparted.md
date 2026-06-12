---
title: "[SOLVED] Need help with gparted"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by tad1073 on 2008-01-11
dev/ida/c0d0=16.94gb unallocated file system unknown disk label type unrecognized
/dev/sdb3= 7.81mb unallocated file system unknown disk label type msdos
unallocated=8.46gb file system unallocated disk Label Type msdos
Help I don't know what I am doing. This system is going to run BIOS and ubuntu only.
Pentium III 733Mhz 256mb ram
Proliant ML330
Compaq Smart Array 431 Controller w/ 265kb cache
Parellel SCSI Array A
Logical Drive 1 ( 16.9GB. Raid 5)
Three 9.1GB (Parellel SCSI) on port 1
Bus interface 64-bit PCI

---

### Post by mrphud on 2008-01-11
If you are going to run ubuntu only why dont you just freshly install the os?

---

### Post by Amstell on 2008-01-11
Allocate 1gb for swap and the rest for ubuntu.  Don't complicate things man.

---

### Post by tad1073 on 2008-01-11
I don't know what i am doing. i tried to install ubnutu but it hangs at 46%. It is a RAID0 set-up by the way.

---

### Post by Amstell on 2008-01-11
sorry i'm not familiar with raid but here is a post to help you out.

[http://ubuntuforums.org/showthread.php?t=630644](http://ubuntuforums.org/showthread.php?t=630644)

Good luck.

---

### Post by tad1073 on 2008-01-11
I gor ubuntu installed but when I rebooted it said there was no os installed. I need someone to hold my hand and walk me through this. More info in a bit...

How do I mount the drives that Ubuntu is on?
Compaq BB009222B5
/dev/sbd1 ext3 2.74GiB /2.56GiB unused
/dev/sdb2 ext3 4.47GiB /2.45GiB unused -Boot
/dev/sdb3 unknown 1GiB
/dev/sdb4 extended 266.7MiB
/devsdb5 linux-swap 266.67MiB

Compaq Smart Array
dev/ida/c0d0 
uallocated unallocated 16.94GiB

---

### Post by antoz on 2008-01-11
These two links offer a lot of help
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by tad1073 on 2008-01-11
Look, I don't mean to sound like an a--hole but I have been trying to get Ubuntu installed on this machine for about 3 weeks now. I am a nood to linux, command prompts, terminals etc. I don't know how to partion where it will work when I boot, I got 16.9GiB's of an array I don't know how to format I am stupid I don't know how to do this stuff. i need live help.

Windows 2000 was on the machine until I changed it from a RAID5 to a RAID0  ](*,)

From gparted i did this:
/dev/sdb2
/dev/sdb4 extended 1GiB
/dev/sdb5 linux-swap 1Gib

---

### Post by Sef on 2008-01-11
> have been trying to get Ubuntu installed on this machine for about 3 weeks now. I am a nood to linux, command prompts, terminals etc. I don't know how to partion where it will work when I boot, I got 16.9GiB's of an array I don't know how to format I am stupid I don't know how to do this stuff. i need live help.


1) Read the tutorials.  If there is something on them that you do not understand, then please post your question or questions in the forum.

2) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download? (Checks the download was good.)

3) Did you burn the iso as an iso? (People sometimes have burned the iso as a data disk.)

4) Did you burn the iso at 4x or less? (Faster may corrupt the download.)

5) Did you check your disk with 'Check Disk for Errors'?  (Instead of starting/installing, go down to 'Check Disk for Errors.)

6) If you got the disks from Ship-It, a friend, or another way, still do step 5.  (Those disks could be bad too.)

---

### Post by bwtranch on 2008-01-11
Sorry tad, for your prob don't really know why, should work from what you have said. You might try a fresh burn of 7.10. Make sure it's a fresh brew with no sugar. Make sure there are no issues with the brewmaster. OK enough of the jargonese, I think just try a new install and make sure the hardware is in order. It should work fine if there are no conflicts.

---

### Post by tad1073 on 2008-01-11
> **Sef said:**
> 1) Read the tutorials.  If there is something on them that you do not understand, then please post your question or questions in the forum.

2) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download? (Checks the download was good.)

3) Did you burn the iso as an iso? (People sometimes have burned the iso as a data disk.)

4) Did you burn the iso at 4x or less? (Faster may corrupt the download.)

5) Did you check your disk with 'Check Disk for Errors'?  (Instead of starting/installing, go down to 'Check Disk for Errors.)

6) If you got the disks from Ship-It, a friend, or another way, still do step 5.  (Those disks could be bad too.)

The disk is from ubuntu. I received it a couple of days before christmas and have been tring to get it on that machine since. I just order the text based installer disk a couple of days ago.

---

### Post by tad1073 on 2008-01-11
> **bwtranch said:**
> Sorry tad, for your prob don't really know why, should work from what you have said. You might try a fresh burn of 7.10. Make sure it's a fresh brew with no sugar. Make sure there are no issues with the brewmaster. OK enough of the jargonese, I think just try a new install and make sure the hardware is in order. It should work fine if there are no conflicts.
I am trying a clean install now.

---

### Post by tad1073 on 2008-01-11
No beans. I might as well use that computer as a boat anchor.


dev/ida/c0d0=16.94gb unallocated file system unknown disk label type unrecognized
I try to set the disk label type but nothing happens, it just hangs up. i give up!!!

---

