---
title: "Some Success for PowerPC"
date: 2010-11-06
forum: Apple Hardware Users
---

### Post by Nonmouse on 2010-11-06
I've recently downloaded the Ubuntu 10.10 for powerpc.  I have a MacMini with a PowerPC G4 1.5GHz.  I saw that they don't advise USB installation, so that was a challenge.

I took a 1GB USB drive and formated it into Mac OS Extended (Journaled) using OS X 10.4.11.  I took my fresh download of Ubuntu 10.10 and extracted the whole .iso file onto the USB drive.

With some tinkering and floating around on the internet, here's what I've been able to do.

Change /install/ofboot.b in TextEdit.  Go to line 11, where it says boot cd:,\install\yaboot, change this to boot ud:,\install\yaboot.

NOTE: not all of the Apple PowerPC machines will allow this to work apparently.  You need to have an OpenFirmware that recognizes USB drives.

Boot into OpenFirmware by pressing the Option-Command(Apple button)-O-F after rebooting.

Again, after much tinkering around on the net and O.F....

type boot ud:\install\ofboot.b and press enter

After a few moments I saw linux boot up and show me Ubutnu 10.10, but not in a GUI. It booted into BusyBox v1.15.3.  It gives an error as follows...

(initramfs) Unable to find a medium containing a live file system

I believe this occurred because it for some reason cannot use the init and cdrom directories.  When I type cd /init or cd /cdrom, it gives me the error of "can't cd into init (or cdrom)"

So, now what?  I haven't thought about what to work on trying next, or if anything is possible at this point.

Just thought I'd share.  Feel free to comment.

---

