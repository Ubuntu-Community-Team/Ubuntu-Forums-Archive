---
title: "Automount USB drive to alternative location"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Harvs on 2007-12-02
Hi

I have a printer with onboard card reader. When I insert a card, it is recognised and mounts automatically.

However, I want to automount it to a different location. I've gone into the disk properties  and under the Volume section entered a new mount point (/storage/printer).

However, when I re-insert the card I get an error message:

Cannot mount volume. Unable to mount the volume. mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

Any ideas?
Thanks

---

### Post by vanadium on 2007-12-02
Instead of /storage/printer just fill in printer. The automatic mounting is always in media. If you specify anything else than a simple label here, mounting won't work (but the graphical UI does not give a warning if you provide an invalid entry)

---

### Post by Harvs on 2007-12-03
Ah, I see. Thanks for explaining this...
Cheers
James

---

### Post by vanadium on 2007-12-03
...been a victim of this small useability issue myself ;)

---

### Post by ShutterAce on 2007-12-11
Should have read this first before changing the mount point in the GUI.:(

Anyway, my question is where/how can I change the entry now that I can't mount my drive?

Thanks!

---

### Post by vanadium on 2007-12-11
"disk properties and under the Volume section": the issue is that you can only enter one label here, not a path. Gnome will happily let you fill in a path, but after that, the mounting is broken.

I prefer changing the name under which an external device loads through changing the file system label.

---

### Post by ShutterAce on 2007-12-11
I knew that :^P

I got it mounted using ntfs-3g and got it changed.

Thanks

---

