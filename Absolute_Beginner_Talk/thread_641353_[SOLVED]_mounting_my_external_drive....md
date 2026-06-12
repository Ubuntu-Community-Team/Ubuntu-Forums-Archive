---
title: "[SOLVED] mounting my external drive..."
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-12-15
i just don't get it.

I keep getting this HAL error.

I got it for seagate, but now with acomdata??

I can't safely remove in windows vista for some reason...

any advice? The show up but I can't mount them

_EDIT: **The Fix**_

Install ntfsprogs from synaptic and then run ntfsfix on your NTFS partition.

> sudo apt-get install ntfsprogs

> fdisk -l

> ntfsfix /dev/sdc1?

Yay :) To fix those stupid NTFS drive errors!

---

### Post by toddward on 2007-12-15
Any chance you could be a bit more clear about the issue?

---

### Post by staticvoid on 2007-12-15
yeah, once I get back on my linux box

---

### Post by staticvoid on 2007-12-15
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-10.png[/IMG]

this help?

---

### Post by staticvoid on 2007-12-16
bump

---

### Post by staticvoid on 2007-12-16
Does this help?

> fdisk -l

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20b9746a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       15298   122881153+   7  HPFS/NTFS
/dev/sdc2           15300       25498    81923467+   7  HPFS/NTFS
/dev/sdc3           25499       33147    61440592+   7  HPFS/NTFS
/dev/sdc4           33148       38246    40957717+   7  HPFS/NTFS


---

### Post by vanadium on 2007-12-16
It is all in the dialog: if yo have windows, follow option 1. If not, I can give more explanation on option 2, forced mounting.

What happened is that your ntfs volume is not "clean", i.e. it has not correctly been disconnected from a Windows  session. Option 1 suggests you to boot back again into Windows, then use the tray icon to disconnect the drive, then shut down windows correctly and boot back into Ubuntu. This would "fix" the drive. Option 2 shows a way to get access to your data anyway, but it is just an "emergency" option in case you do not have (access to) windows but still need to read the ntfs disk,

---

### Post by staticvoid on 2007-12-16
oops.

Looked all geek to me. I shoulda read it.

I can't safely remove under vista, I'll ty on an XP. Does force mounting do any damage?


thank you a ton for explaining that to me

---

### Post by staticvoid on 2007-12-16
hmm, now its giving me this:

> ~$ sudo mount -t ntfs-3g /dev/sdc2 /media/N -o force
[sudo] password:
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/N: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdc2 (N)


looks like I'll have to try option 1...

static

v

---

### Post by vanadium on 2007-12-17
First create your mount point before trying to mount. The mount command complains that the mount point N (just a (prefereably empty) directory) does not exist.

Forced mounting *can* possibly do damage. If I were you, I would mount read-only using the standard ntfs driver, not ntfs-3g. The two commands needed to mount thus would become:

sudo mkdir /media/N
sudo mount -t ntfs /dev/sdc2 /media/N -o force

This will mount your drive read-only in the directory /media/N

---

### Post by kpkeerthi on 2007-12-17
Install **ntfsprogs** from synaptic and then run **ntfsfix** on your NTFS partition.

---

### Post by staticvoid on 2007-12-17
Thanks guys,

I'll test it out. You really gave me some options :)

sv

---

### Post by staticvoid on 2007-12-17
awesome!!!

> ntfsfix /dev/sdc4

Did the trick :)

Thank you

---

