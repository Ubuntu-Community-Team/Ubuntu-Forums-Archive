---
title: "Triple Boot - Ubuntu,OSX, XP"
date: 2009-02-21
forum: Apple Hardware Users
---

### Post by nkentish on 2009-02-21
Problem - when loading XP/Ubuntu from rEFIt when it gets to grub usb keyboard won't let me select options (had same problem with PC box resolved by using PS2 keyboard) but can't do that on iMac dual core with USB only. So it loads osx & ubuntu fine but can't access xp (unfortunatey i still need it but ubuntu rocks!) rEFIt sees all 3 operating systems but when xp or ubuntu are selected it loads grub which always defaults to Ubuntu with no keyboard control. Help?

---

### Post by cyberdork33 on 2009-02-21
> **nkentish said:**
> Problem - when loading XP/Ubuntu from rEFIt when it gets to grub usb keyboard won't let me select options (had same problem with PC box resolved by using PS2 keyboard) but can't do that on iMac dual core with USB only. So it loads osx & ubuntu fine but can't access xp (unfortunatey i still need it but ubuntu rocks!) rEFIt sees all 3 operating systems but when xp or ubuntu are selected it loads grub which always defaults to Ubuntu with no keyboard control. Help?
I think this problem was fixed in a firmware update awhile back. Make sure that you have all your updates in OSX.

If you install GRUB to the Ubuntu partition rather than the MBR (and put the Windows Bootlaoder back in the MBR using FIXMBR) then you can boot into either directly from refit.

---

