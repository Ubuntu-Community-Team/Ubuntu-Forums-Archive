---
title: "/home 78% full with 9% content"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by davidpbrown on 2007-08-08
I have /home on a separate partition ~14GB.. I deleted a big chunk of data as root and now df suggests /home 78% full where graphical Disk Usage Analyser suggests the ~9% I'd expect for the 1.5GB files that remain.

I can't see the root has /.Trash

Is there a way to force a recount of the free space, or are root deleted files really hidden somewhere?

I've done a /forcefsck and reboot..

---

### Post by BaffledMollusc on 2007-08-08
Did you delete it from command line or using Nautilus? If it was Nautilus it's probably a trash problem. I'm not sure where root's trash hangs out.

The other option is, have you checked /lost+found/ and /home/lost+found/?

---

### Post by lisati on 2007-08-08
Sometimes "trash" is hidden from the command line.

---

### Post by ThrobbingBrain66 on 2007-08-08
/root's Trash is located in /root/.Trash.

---

### Post by davidpbrown on 2007-08-08
Thanks for the quick responses.

I'd deleted through Nautilus and I've just found the Trash at
  /home/.Trash-root
not at /root/.Trash as I'd expected

---

