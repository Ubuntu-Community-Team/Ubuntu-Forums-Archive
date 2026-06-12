---
title: "[SOLVED] Mounting"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by natman on 2008-01-21
Hi,
I have switched to KDE, and now my usb stick wont mount, works fine in gnome, any ideas.

Thanks:

---

### Post by dannyboy79 on 2008-01-21
could you be more specific? are you trying to manually mount it? when you plug it in, what does the following return when you enter it a command prompt (terminal) 

tail dmesg

you didn't add an entry in your fstab for it did you? it should be getting automounted. unless there's a setting in the preferences that got unchecked for auto-mounted external drives.

---

### Post by natman on 2008-01-21
i put into a terminal sudo umount /dev/sdb1 and unplugged and replugged and now it works. But i have no simple way to umount it, bar the terminal, in gnome its right click on icon and umount. but in KDE i cant find this, no disk icon appear s on the desktop

---

### Post by natman on 2008-01-21
Ok i finally found out my problem, to check if the usb drive is being mounted:
[HTML]sudo umount /dev/sdb1[/HTML]
or whatever your usb drive is called, then unplug and replug it, a window should pop up, to see the icon on the KDE desktop, right click on desktop -> configure -> behaviour -> device icons, make sure the removable storage device is checked, then log out and back in and it should be there, now right click on icon for safe removal.

---

