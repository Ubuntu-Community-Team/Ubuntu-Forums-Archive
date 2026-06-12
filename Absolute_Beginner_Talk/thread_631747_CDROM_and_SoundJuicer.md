---
title: "CDROM and SoundJuicer"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by wildrain on 2007-12-04
Hi Everyone

Well, the two were working together just fine, I fiddles with the BIOS settings, rebooted, SoundJuicer didn't respond so I reset the BIOS back rebooted, and still get the same message. 

Sound Juicer could not extract this CD.
Reason: Access denied

I checked fstab, and the settings are noauto, butsystem/preferences/... are set to mount when inserted.

I check the properties on the CDROM and it is not mounted, but will play music CDs.

Thanks for your help

Wild Rain

---

### Post by m0biu5 on 2007-12-04
Can you paste the contents of /etc/fstab? More specifically, the line that contains information about your cdrom?

---

### Post by wildrain on 2007-12-05
Here it is...thanks so much for the help...wildrain

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=e3e145c8-192d-4c65-909a-2a93ea2d564d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=10d17bca-98f3-4411-9b04-5ba0042f917f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by ArtInvent on 2007-12-05
I had issues with SoundJuicer, as well as burning CD's. I tried basically all of the various ripping and burning apps available and I eventually settled on K3B from the KDE world. It's pretty great actually, though a little more complicated than SJ for just plain ripping. You might try it or some other ripping app and see if you are able to rip. 

If you're still not able, it may be an issue with user permissions or groups and your group not having the right access to CD-ROMs. As an administrator you can check of which user and which groups have access to peripherals like CD drives, so definitely check that first, I have actually seen these setting get messed up for mysterious reasons.

---

### Post by wildrain on 2007-12-06
Thanks for the reply...I'm going to try  K3B in a few...but I did change some settings in FSTAB today and rebooted in generic diagnostic mode. When FSTAB executes it fails on an error "known file system." The command EXEC was flagged, I removed EXEC the AUTO became the "unknown file system". It's like I'm missing some syntax or something....

Thanks ArtInvent!!! K3B worked wonderfully...but (oh well you already know computers)

I wanted to rip to MP3..I guess that uses LAME, but all I could find was a distribution using tar format and not .deb

I have never done what I think I remember makefile... could some one help...maybe walk through???  Thanks, Wildrain

---

