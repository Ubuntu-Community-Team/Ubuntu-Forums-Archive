---
title: "read USB pen drive"
date: 2004-10-28
forum: Apple PPC Users
---

### Post by vj2k on 2004-10-28
hi,
How can i read a usb pen drive, it does not get automatically mounted aka mac
vijay

---

### Post by Castaa on 2004-10-28
[QUOTE=vj2k]hi,
How can i read a usb pen drive, it does not get automatically mounted aka mac
vijay[/QUOTE]That strange because it mounted my iPod without a problem via a USB connect to by iBook.
 
It didn't auto-mount when I tried ot use the 'firewire' (ieee 1394) connection.

---

### Post by phoolgobi on 2004-10-28
[QUOTE=vj2k]hi,
How can i read a usb pen drive, it does not get automatically mounted aka mac
vijay[/QUOTE]

on fc2 this is what my /ect/fstab reads =>
/dev/sda1 /mnt/pen vfat noauto,users 0 0

when i plug in my pen drive i fire up a terminal and execute =>
$ mount /mnt/pen

hope this helps...

---

### Post by TekMate on 2004-10-29
[QUOTE=Castaa]That strange because it mounted my iPod without a problem via a USB connect to by iBook.
 
It didn't auto-mount when I tried ot use the 'firewire' (ieee 1394) connection.[/QUOTE]
 That's strange on my 867mhz powerbook it showsup on the desktop automatically on insert. What type of system is it?

---

