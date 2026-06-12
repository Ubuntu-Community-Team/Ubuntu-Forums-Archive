---
title: "lost the windows option in grub! help!"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-02-09
I installed some updates that ubuntu prompted me to install, but it changed my grub list and now I don't have my windows option anymore. Does it back up my grub list somewhere so I can copy the windows code back into it?

---

### Post by Shatrat on 2007-02-09
If there is a backup it would be at /boot/grub/menu.lst~ or something like that.
If not you can add a windows entry to look something like this.
```
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
Where hd0,0 will likely vary depending on what partition windows is on.  hd0,0 corresponds to hda1 in the usual linux lingo.

---

### Post by r4ik on 2007-02-09
Try,

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Good luck !

---

### Post by -Ghost9- on 2007-02-09
found it thanks!

---

