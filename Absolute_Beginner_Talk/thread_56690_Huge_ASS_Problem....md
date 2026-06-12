---
title: "Huge ASS Problem..."
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by Muhammad on 2005-08-13
I've just installed the nVidia driver, and I was supposed to reboot using Ctrl+Alt+BackSpace, when I did so, everything halted and I had to reset manually...

I recieved this error right after GRUB finished loading...

> Starting Ubuntu
Starting Splashy Boot Sequence
*Mounting a tmpfs over /dev
*Creating Intial device nodes...
*Setting disc parameter
/dev/cdrom: No such file or directory
*Checking root or file system
/contains a file system with errors, check forced
Inode 2367297 has imagic flag set

/unexpected Inconsistency; run fsck Manually
[COLOR=Red]*[/COLOR] (ie: without -a or -p options)

[COLOR=Red]*[/COLOR]fsck failed, please repair manually and reboot. please note that root file system is currently read-only to remount it read-write:
```
# mount -n -o remount,rw/
```

Control-D will restart

Question is: What should I do to fix this? or should I re-install Ubuntu? or maybe go back to WinXP?

NOTE: I only have one hd with everything set to default during installation.

---

### Post by az on 2005-08-13
CTRL-ALT-BAckspace does not reboot.  It restarts  your X server.  It probably was misconfigured and you had a black screen.

Was this a fresh install?  I ask because it looks like you may have some data loss.

---

### Post by Muhammad on 2005-08-13
It is a fresh install, anyway, I formatted and re-installed the whole thing now. Apperantly the problem was unsolveable.

New Question: Is it possible to install Windows after installing ubuntu? or should I re-format, install windowsXP, then re-install Ubuntu...?

---

### Post by Ampersand on 2005-08-14
Windows tends to assume it's the only OS on the computer, and so rewrites the MBR, making it quite a bit harder to get into Ubuntu. It's probably easiest to install windows first.

---

