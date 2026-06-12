---
title: "how to safely remove usb flash drive? (Solved)"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by lintroduccion on 2006-10-11
A simple question.

In windows, I had "safely remove" my usb flash drives before removing, so its contents doesn't corrupt. Is the same operation necessary/available in (X)ubuntu?

I couldn't find any options related to, so I'm just "unmounting" it before removal. Are these the same?

Oh, I'm running Xubuntu Dapper, if there's any differences compared with Ubuntu:).

---

### Post by aysiu on 2006-10-11
Right-click the drive and unmount it. That's safely removing it.

---

### Post by lintroduccion on 2006-10-11
Thanks:).

---

### Post by aysiu on 2006-10-11
P.S. The drive won't disappear from Thunar until you actually physically remove the drive.

Some drives have a light that turns off in Windows but not in Ubuntu. The drive is still safe to remove if it's unmounted. The difference is that Windows unmounts the drive *and* turns off the power to it. Of course, once you unplug the drive, the power turns off, too.

---

### Post by TiredBird on 2006-10-14
I've been using pen-drives, (flash-drives, thumb-drives, whatever), on Windows, Ubuntu and now on Xubuntu. I have learned a few things that might help out.

(1) If the amount of writing to the pen-drive is fairly small, mount it with 'sync' as an option (either in fstab or the mount command). That way each write gets closed out immediately.

(2) If you have a big transfer of data to the usb-pen-drive, take the 'sync' option off at least temporarily or it will take forever to do the writing, (maybe as much as 10 times as long).

(3) Before removing the pen-drive, do a 'sync' from the command line and wait for the command prompt to come back before pulling out the drive. (When I have done a large transfer, like an 'rsync' 300 MB write to the pen-drive, it has taken as much as a minute or two for the system to finish the transfer. In the meantime, the 'sync' command will not give you a new command prompt.

The foregoing is based on experience, not any particular technological knowledge so it may be incorrect. If so, I'm sure one of the experts will correct me.

---

### Post by sicofante on 2007-02-05
Shouldn't the OS take care of all these?

---

