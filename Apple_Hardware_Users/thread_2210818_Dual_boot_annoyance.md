---
title: "Dual boot annoyance"
date: 2014-03-12
forum: Apple Hardware Users
---

### Post by jstew1974 on 2014-03-12
Greetings,

I'm running Ubuntu 13.10 and OS X Mavericks in dual boot mode. I'm running in EFI mode, booting straight to grub as described here:

[https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)

This works great. MUCH better than using BIOS emulation and a hybrid MBR. I can boot into Ubuntu just fine after install, shut down, reboot. But as soon as I boot into OS X, I'll reboot, and it will boot straight into OS X again instead of grub. After doing a bit of research, I find that OS X is modifying the boot order in EFI back to MacOS first. I can repair this by booting up with a live usb, running efibootmgr and changing the order back to Ubuntu first. 

This is annoying. Is there a way that I can keep OS X from modifying the boot order? I want to be able to boot OS X from grub and I don't want to install refit or refind.

---

### Post by este.el.paz on 2014-03-14
> **jstew1974 said:**
> Greetings,

I'm running Ubuntu 13.10 and OS X Mavericks in dual boot mode. I'm running in EFI mode, booting straight to grub as described here:

[https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)

This works great. MUCH better than using BIOS emulation and a hybrid MBR. I can boot into Ubuntu just fine after install, shut down, reboot. But as soon as I boot into OS X, I'll reboot, and it will boot straight into OS X again instead of grub. After doing a bit of research, I find that OS X is modifying the boot order in EFI back to MacOS first. I can repair this by booting up with a live usb, running efibootmgr and changing the order back to Ubuntu first. 

This is annoying. Is there a way that I can keep OS X from modifying the boot order? I want to be able to boot OS X from grub and I don't want to install refit or refind.

Short answer, no, I on't think you can do dual boot w/o . . . in your case, you would need rEFInd to work with Mav . . . because from what I've seen, indeed OSX "takes charge" of things and messes with the linux GRUB stuff.  It's not a big deal to use rEFInd . . . it's free, works well . . . it just takes a bit of reading to get the install right . . . from OSX side . . . .

e.e.p.

---

