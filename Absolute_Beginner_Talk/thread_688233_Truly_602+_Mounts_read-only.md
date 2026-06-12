---
title: "Truly 602+ Mounts read-only"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by jonnan on 2008-02-05
Before last nights updates (Within the last week or so - this could be coincidental) were processed, My MP3 player mounted fine. After this last 24 hours of updates, all attempts to write to or change permissions of the USB drive of the player show it as a "Read-only file system", including attempts to do so as root (sudo cp a b, sudo nautilus etcetera).

'mount' however shows it as read write 
"/dev/sda on /media/TRULY 602+ type vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)"

I can unmount it fine, and read the files that it has fine (while mounted), I just can't save any new files to it.

I've looked through several other threads on the subject, but it doesn't seem to be an issue resolvable by root access or adjusting permissions, so I'm not seeing any obvious solutions.

Thanks - Jonnan

---

