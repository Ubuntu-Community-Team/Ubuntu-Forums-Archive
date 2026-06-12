---
title: "Booting multiple versions of OSX with Grub2"
date: 2017-10-10
forum: Apple Hardware Users
---

### Post by valvestate163 on 2017-10-10
Hi everyone. It's my first time trying ubuntu/linux in over ten years. I'm trying to figure out how to make multiple OSX entries in grub2 for installs on multiple disks and having issues. One install is on the internal flash, the other on an esata disk connected by thunderbolt (I'm able to boot another install of ubuntu on that disk). Mid-2011 MBA running 16.04 LTS *and OSX 10.10.5 Yosemite, native EFI.

So for the main menu entry for internal flash, it works by search --file, but that makes it load the first OSX booter it finds. I want to force both entries to go by UUID, but it says it can't find the device that way using --fs-uuid. I use insmod part-gpt and hfsplus. I have the correct UUIDs from blkid.

Any ideas? Do I need to hint-efi the disks? I don't want to use RefInd.

---

### Post by kevin160 on 2017-10-11
I've never had good luck with grub's macOS boot facility, so I think you are really rowing upstream by not using rEFInd, but this is interesting.  

If you get it working reliably with 2 different installs, please come back and write a quick summary.  :-)

Me, I'd just hold opt for the case where you need to boot Yos from the external.  But I totally get it if you need to switch OSes remotely or something.

---

### Post by valvestate163 on 2017-10-11
My motto is uphill battle. I'll try a few things and see what I can come up with. I'll post back with results.

---

