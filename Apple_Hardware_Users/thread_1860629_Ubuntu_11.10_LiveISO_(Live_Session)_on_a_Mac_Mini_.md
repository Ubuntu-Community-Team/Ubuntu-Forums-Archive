---
title: "Ubuntu 11.10 LiveISO (Live Session) on a Mac Mini 2011"
date: 2011-10-14
forum: Apple Hardware Users
---

### Post by thecek on 2011-10-14
Hey there,

I would like to know if is it possible to running the new Ubuntu 11.10 in a Live Session (using a USB stick) on the Mac Mini 2011?

I managed to do that on a common PC using a fat formatted USB stick and GRUB 2, and then I've just to put the ISO file inside the stick and add an entry to grub.cfg, but I could not do the same with the Mac yet.

I know that there's a different boot system in mac called EFI, and I also tried the project rEFIt but stil got no success.

Have anyone tried something like that? If so, would you help me on?

Thank you

- CEK

---

### Post by pilb on 2011-11-25
[SIZE=1]From what I have read (but not tried), you should be able to install rEFIt to a flash drive or burn it to a CD.  Look at [http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html) and scroll down to "[/SIZE][SIZE=1]Installing on a separate volume or external disk[/SIZE][SIZE=1]."

Alternatively, you can burn a CD containing the Plop boot manager.  It allows you to boot from USB on computers without BIOS support for USB booting.  There is one drawback: you will be unable to use USB keyboards to interact with syslinux/extlinux/grub/etc. so they must be configured to boot a desirable default after a timeout.  (Be careful - IIRC some options in Plop allow you to wipe partition tables!)  [http://www.plop.at/en/bootmanagerdl.html](http://www.plop.at/en/bootmanagerdl.html)
[/SIZE]

---

