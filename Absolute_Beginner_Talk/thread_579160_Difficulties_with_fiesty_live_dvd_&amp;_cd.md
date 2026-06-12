---
title: "Difficulties with fiesty live dvd &amp; cd"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by mhwilson on 2007-10-18
When running fiesty 7.04 from either the live dvd or cd i get the followint error during the initial boot into the desktop,

error loading 'lib/firmware/bcm43xx_microcode5.fw for device '/class/firmware/0000:05:02.0' with driver' (unknown)' .
I am also getting an error (the number go by too fast to record them)
[several number combos] bcm43xx5.fw error:microcode 'bcm43xx_microcode.fw not avaliable or load failed.

I have located the windows drivers and have located ndiswrapper to utilize them, but these drivers are on the local hard disk and I cannot get that mounted.  At the "root@ubuntu: /home/ubuntu# mount /dev/hda(1)"
I get---
mount: can't find hda(1) in /etc/fstab or /etc/mtab
the same with cdrom

fdisk -l (shows the drive)
Disk /dev/hda  then list information th t is correct.

I have utilized the Official documentation, the forums including starman's install guide, to no avail.  I have also checked the md5 hashes and verified the disk using the provided tool.
What now?
:icon_frown:


I was very impressed with knoppix and now I want to be a kubuntu convert, but I need to be able to get it to work from the Live cd/dvd first.


Thanks so much

---

### Post by mhwilson on 2007-10-18
OOPS, my bad.
The credit for the Install Guide should be Starcraftman not starman.
Sorry.
:oops:

---

