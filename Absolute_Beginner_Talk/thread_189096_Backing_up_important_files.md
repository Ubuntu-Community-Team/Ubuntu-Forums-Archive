---
title: "Backing up important files"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by hastalavista on 2006-06-04
I'm new to Ubuntu and Linux, and I was wondering what files besides /etc/X11/xorg.conf are important to back up. Also, in the event that the operating system crashes and won't come up, can I boot directly from the Ubuntu CD to restore the system to it's previous setup using these files?

Thank you,

Dave

---

### Post by jpkotta on 2006-06-04
Probably the easiest way to back up your settings is with ```
cd / ; sudo tar zcvf etc.tar.gz /etc
``` which creates a tarball of /etc, the settings directory.  There are settings that are not in /etc, but most are.  You might as well back up the whole thing, because /etc is not that big and compresses pretty well.

You can almost always recover the system, short of a file system corruption or hard drive crash.  And the best way to do this if the system is unbootable is to do as you said, use the CD and pick recovery mode.

Note that the files controlling the boot loader (grub) are in /boot/grub, so it is a good idea to back up /boot as well.

---

### Post by hastalavista on 2006-06-04
Thank you for the quick reply. I must admit that my present Dapper OS is working well even after installing/uninstalling a bunch of programs. Therefore, I wanted to save my settings before I screwed something up.

---

### Post by jpkotta on 2006-06-05
FYI, by default, settings are not removed when a package is uninstalled (and I think that settings are not replaced when reinstalling).

---

