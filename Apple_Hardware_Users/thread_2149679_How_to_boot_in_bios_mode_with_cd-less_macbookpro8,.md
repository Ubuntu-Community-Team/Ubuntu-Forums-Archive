---
title: "How to boot in bios mode with cd-less macbookpro8,2"
date: 2013-05-29
forum: Apple Hardware Users
---

### Post by miguelnegrao on 2013-05-29
Hi

I want to get my radeon card working on a macbookpro8,2. To do that I need to boot in bios mode and dump the bios. I don't have an internal cd drive (removed and changed to another harddrive). I tried booting from cd using an external cd drive, I hit alt, then select the cd incon  that says "windows" but I get an error message, something like "No operating system found" and I never get to the grub menu... I tried also with a 32bit ubuntu on a usb pen and got the same error... Is it possible at all to boot in bios mode without an internal cd drive ?

thanks,
Miguel

---

### Post by Egon058 on 2013-05-30
Hi Miguelnegrao,

Of course you can boot without a internal CD drive ! Actually I don't know how you've made your USB Boot key, but if you follow [these]("http://www.nightlionsecurity.com/blog/guides/2011/07/burn-iso-to-bootable-usb-flash-drive-in-mac-osx-terminal-via-command-line-diskutil/#.UadGdevywXw") instructions with the 64 Bits disk image of Ubuntu 12.04.2 (LTS), you'll normally be able to boot on it.

Three things more :
- First, at step 3 of the tutorial, you'll create a disk image named "blablabla.img.dmg" (as said, OSX will automatically put the .dmg extension at the end of the file). You just need to remove the .dmg extension at the end of the file to have your .img image.
- When finishing your key, your Mac will say that it can't read it. Just eject the key...
- When booting, holding your "alt" key, two yellow disks will show up (it was the case for me). Just select the left one and Ubuntu will start.

Hoping this might be helpful !

Good luck !

---

### Post by miguelnegrao on 2013-05-30
Yes, I can boot with a usb key in efi mode, but I've never been able to boot in bios mode with either cd or usb pen. 

It doesn't matter, I've managed to get the radeon card working by booting with efi boot stub directly from refind without grub. It's incredible that this info is not on the macbookpro8,2 wiki...

---

