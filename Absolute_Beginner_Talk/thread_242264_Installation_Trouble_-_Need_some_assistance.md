---
title: "Installation Trouble - Need some assistance"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by jscam on 2006-08-23
Hi - I am trying to install and I got as far as botting up the live cd and then it stalls on the screen with 

"Uncompressing Linux... Ok, booting the Kernel"

So I restarted and booted with the options "noapic nolapic" under F6 and then it got a little further and stalled with:

"Uncompressing Linux... Ok, booting the Kernel.
[17179829.128000] Buffer I/O error on device hdc, logical block 151534

VFS: brelse: trying to free free buffer (6 more times)

SQUASHFS error: sb_bread failed reading block 0x492fd
SQUASHFS error: unable to read fragment cache block [124b932c]
SQUASHFS error: unable to read page, block 124b932c, size []

And now windows will not start - just stalls out on starting windows in safe mode or start windows normally screen???

Any help - I think I just crashed everything.

---

### Post by cptjaben on 2006-08-23
This may not be of much help to you, but if I were you I'd wipe  your harddrive(after backing up your files) and do a fresh install of windows and then a fresh install of ubuntu. as far as getting your files off your hardrive, you might be able to run a live cd of ubuntu and back them up on a disc. Hope this helps

---

### Post by Fully216 on 2006-08-23
Sound like part of your hard drive has problems/errors.  I would perform a disk check to ensure the integrity of the drive.  Based on your specific hardware, you can find the resources you need here:

[http://www.tacktech.com/display.cfm?ttid=287](http://www.tacktech.com/display.cfm?ttid=287)

I hope that you backed up your data before you tried the install.  If not, I would recommend doing so by running the live CD.  Being able to run the live CD also indicates it probably is a hard drive issue.

Hope this helps ;)

---

### Post by jscam on 2006-08-23
Thanks for the advice - I will take a look at the HD and see if that is the issue  - thanks for the site rec. - I am messing around on this PC - so if I crash it, no prob.  Just trying to learn my first linux.

---

