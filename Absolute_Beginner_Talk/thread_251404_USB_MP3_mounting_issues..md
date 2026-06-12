---
title: "USB MP3 mounting issues."
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by underwaterbob on 2006-09-05
Ok, I mount my iriver U10 and cannot write to it.  dmesg gives me this:

[17179674.112000] USB Mass Storage support registered.
[17179679.112000]   Vendor: iriver    Model: U10               Rev: 1.00
[17179679.112000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179679.124000] usb-storage: device scan complete
[17179679.156000] Driver 'sd' needs updating - please use bus_type methods
[17179679.156000] SCSI device sda: 3976875 512-byte hdwr sectors (2036 MB)
[17179679.160000] sda: Write Protect is off
[17179679.160000] sda: Mode Sense: 03 00 00 00
[17179679.160000] sda: assuming drive cache: write through
[17179679.204000] SCSI device sda: 3976875 512-byte hdwr sectors (2036 MB)
[17179679.208000] sda: Write Protect is off
[17179679.208000] sda: Mode Sense: 03 00 00 00
[17179679.208000] sda: assuming drive cache: write through
[17179679.208000]  sda:
[17179679.208000] sd 0:0:0:0: Attached scsi removable disk sda
[17179679.220000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179679.624000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179694.784000] FAT: Filesystem panic (dev sda)
[17179694.784000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[17179694.784000]     File system has been set read-only

Is my file system corrupt?  Is there anything I can do?  I've found a lot of information but none of it has helped.  I've edited fstab, remounted manually, tried fsck (Bad magic number in superblock) and finally tried to reformat the whole stinking thing with gparted telling me it couldn't do anything (At first it appeared to be a Fat32 partition.  After unsuccessfully attempting to reformat, it now says it's unallocated).

The really irksome part is it worked fine for about a half a week.

Any help, even a "Yes, I know you are screwed" would be appreciated, I am lost.

---

### Post by chicken101 on 2006-09-05
Try mounting it in amarok, see what happens.

Sorry I couldn't help much, I have no experience with iRivers.

:(

---

### Post by chicken101 on 2006-09-05
Ok, I think I can help you!  I did a little snooping around in synaptic, and I found a couple of packages for irivers.

Install the following (search for them in synaptic)

easyh10
iripdb
libifp4


Hope that helps!:KS

---

### Post by underwaterbob on 2006-09-05
Thank you both but:

Installed Amarok and tried to delete a track on it it said

"Could not start process Unable to create io-slave:  klauncher said: Unknown protocol 'trash'.

I installed the packages mentioned for irivers and a couple others I dug up that just mentioned iriver and still the same results, still the same dmesg (actually more than one invalid cluster chain this time).

Sometimes running "sudo mount -o rw,remount,umask=0755 /media/U10" will allow me to quickly write a small amount of data to the player but then it jumps back to ro pretty quickly.

Is it trash?

---

### Post by underwaterbob on 2006-09-05
Update!

Ran to a PC Bang (Korean Internet cafe) and formatted the thing on an XP machine since Ubuntu seemed loathe to let me do so.  It's now working fine.

I think the problem originated with Ubuntu automatically creating a .trash directory on the USB drive and somehow corrupting the filesystem.  Or I may have disconnected it badly.  The last time I used it when it was working before I was in a hurry...  Have to be more careful of these things running linux now.

Thank you people!

---

### Post by chicken101 on 2006-09-06
No prob.

---

### Post by sinaen on 2006-10-02
have anyone of you experienced that you need to reformat the iriver player every time you connect it?

---

### Post by freeridr on 2007-02-13
> **underwaterbob said:**
> 
Ran to a PC Bang (Korean Internet cafe) and formatted the thing on an XP machine since Ubuntu seemed loathe to let me do so.  It's now working fine.

please tell me how you formatted your iRiver. did you have to install the iRiver software on the machine? it looks like i'll have to do the same thing because amarok won't format and i'm getting a constant "scan for music" loop on power up.

please help me.

---

