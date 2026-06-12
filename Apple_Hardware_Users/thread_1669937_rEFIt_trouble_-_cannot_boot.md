---
title: "rEFIt trouble - cannot boot"
date: 2011-01-18
forum: Apple Hardware Users
---

### Post by qualudeburrito on 2011-01-18
I installed rEFIt on my iMac a while back with intentions of installing ubuntu alongside OSX.  Things were fine for about a year or so.

Today when I attempt to boot my computer, the rEFIt screen comes up, but displays only the grey background and the rEFIt logo with the orange arrows.  There are no menu items at all.  I can't figure out what happened or how to boot my system.

Any ideas are much appreciated!

-C

---

### Post by ZeroLinux on 2011-01-18
You can boot from cd-rom with recorded rEFIt to MacOS (ISO with rEFIt you can take [here]("http://downloads.sourceforge.net/refit/rEFIt-0.14.cdr.gz?use_mirror="), reinstall rEFIt there, and reboot into ubuntu.

---

### Post by srs5694 on 2011-01-18
Try holding down the Option key (or Alt if you're using a PC keyboard) while booting the computer. That should bring up the Mac's native boot loader. With any luck, it'll give you the option to boot an OS X installation or rEFIt.

Another thing you might try, if that fails, is to boot an OS X install disc. You should then be able to set the boot disk using one of the utilities (I don't recall what it's called, though), check your disks for error (with Disk Utility), and even run a Terminal to run various command-line recovery tools.

---

### Post by Hatsune Miku on 2011-01-18
> **qualudeburrito said:**
> I installed rEFIt on my iMac a while back with intentions of installing ubuntu alongside OSX.  Things were fine for about a year or so.

Today when I attempt to boot my computer, the rEFIt screen comes up, but displays only the grey background and the rEFIt logo with the orange arrows.  There are no menu items at all.  I can't figure out what happened or how to boot my system.

Any ideas are much appreciated!

-C

Command + Option + X at boot will force the Macs Firmware to search for a Mac OS X Install. Boot into OS X and just reinstall rEFIt. :)

---

### Post by qualudeburrito on 2011-01-24
Thanks for the replies.  I've been busy so didn't get to respond until now.  

Holding option doesn't override the blank refit menu.  I'll give cmd-option-x a try and if that doesn't work, I'll try the refit boot cd.

I'll post back after I try.

-C

---

### Post by qualudeburrito on 2011-01-25
cmd-option-x worked.  Thanks for the help all.

-C

---

