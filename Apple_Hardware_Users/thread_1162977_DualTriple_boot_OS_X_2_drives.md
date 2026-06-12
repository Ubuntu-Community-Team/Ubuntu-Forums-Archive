---
title: "Dual/Triple boot OS X 2 drives"
date: 2009-05-18
forum: Apple Hardware Users
---

### Post by sscotti on 2009-05-18
Are there instructions on how to install Ubuntu on a system running OS X Leopard with 2 drives.  I have Leopard installed on the internal drive and I have an external firewire drives that I'd like to install Ubuntu and perhaps even Windows XP on.  I tried installing Ubuntu and I got a non-system disk folder error on startup after installing Ubuntu and had to reinstall OS X.  Fortunately, I had everything backed up.

I later saw the post about installed on a single drive but I'm wondering how that applies to a 2 disk system.  Ideally, I would like to triple boot into OS X, Windows XP and Ubuntu.

---

### Post by cyberdork33 on 2009-05-18
installing to an external drive doesn't quite work well yet. You can do it with GRUB-EFI though. Check the FAQ about this. Also check here:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by sscotti on 2009-05-19
Thanks.  Got a triple boot configuration using BootCamp and rEFIt per Lars Strand.  I installed the 64 bit version of Ubuntu 9.x and everything is working but the WiFi.  Any idea on how to get that going?  It doesn't seem to be recognising the device.  I've heard about using NDIS wrapper, but I'm not sure which driver to user and how to install it.  The driver currently installed is the Broadcom driver but that isn't working.  I don't see how to install Windows drivers.  Any thoughts on that.  I'll make a separate post after searching the forums.

---

### Post by cyberdork33 on 2009-05-19
> **sscotti said:**
> Thanks.  Got a triple boot configuration using BootCamp and rEFIt per Lars Strand.  I installed the 64 bit version of Ubuntu 9.x and everything is working but the WiFi.  Any idea on how to get that going?  It doesn't seem to be recognising the device.  I've heard about using NDIS wrapper, but I'm not sure which driver to user and how to install it.  The driver currently installed is the Broadcom driver but that isn't working.  I don't see how to install Windows drivers.  Any thoughts on that.  I'll make a separate post after searching the forums.
I answered in your new thread:
[http://ubuntuforums.org/showpost.php?p=7309443&postcount=2](http://ubuntuforums.org/showpost.php?p=7309443&postcount=2)
[]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages")

---

