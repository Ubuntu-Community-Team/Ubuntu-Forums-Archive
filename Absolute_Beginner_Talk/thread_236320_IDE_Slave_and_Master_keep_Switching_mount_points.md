---
title: "IDE Slave and Master keep Switching mount points"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by HeyGabe on 2006-08-14
When I move back and forth between Ubuntu and WinXP Home sometimes my ide diskdrives will trade places in /media/.
My Ubuntu install is on a 4 GB partition on my 150GB  WinXP drive, which I have set up as the master drive and I have a little 12 GB drive that I use for moving files back and forth. The problem is that sometimes the drives seem to switch back and forth between being /media/idedisk and /media/idedisk-1

This woldn't bug me, but it means the drive shortcuts on my desktop don't point to the right place all the time.

Does anyone have suggestions?

---

### Post by mgor on 2006-08-14
not really sure why they're changing names. but i guess you've created the shortcuts yourself?

remove them, open up gconf-editor, browse apps/nautilus/desktop and mark "volumes_visible".

---

