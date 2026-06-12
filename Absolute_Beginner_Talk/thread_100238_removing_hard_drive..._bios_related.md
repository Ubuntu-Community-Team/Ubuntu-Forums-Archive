---
title: "removing hard drive... bios related?"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Reaped In Half on 2005-12-07
hi, when I upgraded my computer recently, I slapped in a new hd, and left the old one as primary... essentially the new 160gb drive was labeled hdb and the old one is hda.  I deleted the old drive and it is not mounted.  How can I effectively remove it without getting the error that an ide drive has decreased?

---

### Post by jorn on 2005-12-07
Hello!
Terminal:
"sudo cp /etc/fstab /etc/fstab_backup" without the quotes in order to make a copy if you mess up something.
Terminal:
"sudo gedit /etc/fstab" and delete the line with the drive that is missing or put "#" in front of it.
Remenber to save your changes before you close the textfile.
Hope that works.
Regards
Jorn

---

### Post by Reaped In Half on 2005-12-07
I already tried that... the device isn't even listed in fstab.  I'm thinking it's something with the bios.

---

### Post by BatsotO on 2005-12-07
what did you mean by delete? from which device did you boot anyway (hda, hdb or cdrom)?

---

