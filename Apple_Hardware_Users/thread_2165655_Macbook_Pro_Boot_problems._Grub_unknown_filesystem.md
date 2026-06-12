---
title: "Macbook Pro Boot problems. Grub unknown filesystem"
date: 2013-08-05
forum: Apple Hardware Users
---

### Post by sillymesilly on 2013-08-05
I used the boot repair and I still get the same exact problem.
On boot up I get grub> unknown filesystem

Here the link provided by the boot repair
[http://paste.ubuntu.com/5952808/]("http://paste.ubuntu.com/5952808/")

Thank You

---

### Post by oldfred on 2013-08-05
Is this a Mac. That makes it a lot different than a PC. 
I can move your thread to the Apple sub-forum where more users are familar with your Mac issues.

Some possible links.
       MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware](http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware)
Caution on UEFI boot Mac
[http://ubuntuforums.org/showthread.php?t=2012588](http://ubuntuforums.org/showthread.php?t=2012588)

---

### Post by sillymesilly on 2013-08-05
Yes this is a macbook pro. If you can move it to appropriate channel then please do it. Thank you.

---

### Post by oldfred on 2013-08-05
Moved to Apple sub-forum.

---

### Post by r3dbeard on 2013-08-06
Could be running into a MBR (master boot record) limitation that will only allow you to have 4 partitions [eg. EFI, Mac HD, Linux HD, Swap]. I've run to this as well when setting up triple-boot macbook pros with linux and windows; I had to drop the swap partition and move backups to external drives. Hope this helps.

[http://superuser.com/questions/160224/intel-mac-cant-have-more-than-4-partitions](http://superuser.com/questions/160224/intel-mac-cant-have-more-than-4-partitions)

---

