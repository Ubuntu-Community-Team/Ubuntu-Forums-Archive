---
title: "Auto-mount devices on startup"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by mateoc15 on 2007-11-08
I have looked around quite a few different places to find what I'm looking for but have been unable to do so.  I would like to be able to mount a few different NTFS drives *before* the GUI really starts to load (somewhere between login and the desktop appearing, I guess).  I set my desktop background as an image on one of the NTFS drives and would like for it to appear as if I had the file on my desktop or home directory.  I also would like to run some scripts (which would be run after this mounting script) to copy files from one drive to another (ie - runs a copy command to back up some files).

I know the protocol for the mount command and have figured all of that out.  What I'm unsure of is where/how to get the script to run automatically and how to do so before everything begins really loading.

I'm using Gutsy 7.10.

Any ideas?

Thanks in advance!

---

### Post by digitalbenji on 2007-11-08
You don't need to use a script to do this.  Automounting is handled in linux by the fstab file, locate in Ubuntu at /etc/fstab.

You should just open an editor as root and add entries to the fstab file for the filesystems/devices you want automounted.  This will ensure that they are automatically mounted and unounted on boot/shutdown.  

The format of the fstab file is pretty self explanatory, just follor the format of the existing entries, but modify it to suit your needs.  I believe for the filesystem type you will have to use ntfs-3g instead of plain old ntfs.  If you have more questions, let us know.

Thanks

---

