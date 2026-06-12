---
title: "turning off automount for usb mass storage"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by thereallos on 2007-02-09
Hi,
I'm having a problem trying to format my new SanDisk Cruz 2 gig  flash drive.
When I use gparted to to format the drive I have to unmount it before I can queue up any changes, however it seems to automount the drive again when I hit the apply button and gives me an error that says
" /dev/sdc1 is mounted: will not make a filesystem here! "
How do I stop it from automounting and screwing up the filesystem alterations?
Thanks for anyone that can help me.

---

### Post by thereallos on 2007-02-09
turns out this is a known bug in edgy ... 
"You can workaround it by disabling auto-mounting of hot-plugged drives (via System / Preferences / Removable Drives and Media), then creating the file system, and then re-enabling auto-mounting."

fixed

---

