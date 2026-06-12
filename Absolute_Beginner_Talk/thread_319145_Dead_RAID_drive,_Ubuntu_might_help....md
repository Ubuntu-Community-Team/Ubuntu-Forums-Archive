---
title: "Dead RAID drive, Ubuntu might help..."
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by rich.bradshaw on 2006-12-15
My Grandad has a PC with 2 hard drives in RAID 0 config. One of them has died, so he can't boot into Windows, as this is installed on the disks. If I boot from the live CD, I was hoping to be able to mount the drive and an external usb drive and copy over some of the files - he has 99% backed up luckily, but he has some files from the last few days he would like.

Will this work - what do I need to know before I turn up? Will Edgy auto mount the USB drive, and the Raid or will it need special drivers? I am hoping that even though the fs is corrupt I might be able to read some data from it... any ideas? I'm going over tomorrow morning (I'm in the UK) so I have around 24 hours to get as much useful info as possible!

If the RAID doesn't auto mount, should I assume that it is completely dead?

---

### Post by xyz on 2006-12-15
For a start, this would surely come in handy:
[SystemRescueCd]("http://www.sysresccd.org/Main_Page")
> Description: SystemRescueCd is a linux system on a bootable cdrom for repairing your system and your data after a crash.....
Good luck to you and your Grandad.

---

### Post by rich.bradshaw on 2006-12-15
Is there anything in there that isn't in Ubuntu? I have limited internet per month, so don't want to be downloading whole new cds if possible.

Really I suppose I want to know if a Dell OEM Raid 0 drive will be picked up by Ubuntu, and what to try if it isn't.

---

### Post by psusi on 2006-12-15
If it was raid0 and one drive is totally dead, then all your data is gone.  I hope you have backups.  

That is the drawback of raid0: the data is spread out across the drives, so if you loose one, you loose all the data.

---

### Post by rich.bradshaw on 2006-12-15
That's what I imagined  - is there a possibility that only part of the drive is damaged and the rest is recoverable? Will I be able to mount it forceably in any way?

---

### Post by psusi on 2006-12-15
It is possible.... try booting the livecd and run badblocks on both drives ( if they show up ).

---

### Post by rich.bradshaw on 2006-12-15
What do I do with the output of badblocks? Both drives will be formatted as NTFS.

---

### Post by rich.bradshaw on 2006-12-16
Anything else I can try - I'm leaving in a couple of hours to go help him!

---

### Post by xyz on 2006-12-16
> **rich.bradshaw said:**
> What do I do with the output of badblocks? Both drives will be formatted as NTFS.
Hi,
Have you read this:
[What to do if you have a bad superblock]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_on_a_FAT32_")
Hope it's not too late!

---

### Post by rich.bradshaw on 2006-12-16
No still got time!

Thanks for all your help!

---

### Post by psusi on 2006-12-27
If the drive has bad blocks, you should replace it.

---

