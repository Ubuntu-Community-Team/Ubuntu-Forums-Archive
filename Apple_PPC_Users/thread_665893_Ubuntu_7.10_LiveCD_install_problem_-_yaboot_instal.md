---
title: "Ubuntu 7.10 LiveCD install problem - yaboot installation fails"
date: 2008-01-12
forum: Apple PPC Users
---

### Post by andyman11 on 2008-01-12
I'm a Linux noob trying to put Ubuntu 7.10 on an external drive connected to my 1 ghz PowerBook G4. It's a 320 GB drive with about 100 GB partitioned with Disk Utility for use with Mac files(HFS+ I think), then the rest is left as unallocated free space. 

LiveCD boots fine, the external drive is detected, the partitions I need seem to be created and installation goes fine up until it's about 95% complete and it fails to install yaboot on the "New World bootstrap" partition. Then I receive a warning that the system may not be bootable. 

I'm pretty sure something is going wrong in the partitioning process, though I've gone back and tried several different partitioning options in both GParted and the manual partition step of the installation. 

Can anyone walk me through how to set up the New World bootstrap partition correctly? There seems to be two "New World" options in the manual partition step of the installer, and neither works for me in the end. I don't see any way to specify a partition as "new world" in GParted.

---

### Post by stream303 on 2008-01-19
It can be done, but it's a bit hairy.  I wrote this up back in the edgy days.  Not so sure I'd go through all that pain again, but it might help:

[http://ubuntuforums.org/showthread.php?t=314237](http://ubuntuforums.org/showthread.php?t=314237)

---

