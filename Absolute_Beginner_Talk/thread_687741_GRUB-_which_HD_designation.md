---
title: "GRUB- which HD designation?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by badbob100 on 2008-02-04
I'm installing Ubuntu 7.10 64 bit (or trying to) the 8GB partition on the 120GB HD, with a 2GB swap file. Windows is installed on the 250GB HD. The default GRUB bootloader is HD0, so I leave it to that- when I finish Ubuntu install and reboot it just boots into Windows, with no OS boot options.

What HD0-5 do I need to enter for it to install the grub loader onto the 250GB? Why isn't there a drop down box with specfic HD option in GRUB bootloader, like partition manager?

[IMG]http://i47.photobucket.com/albums/f184/badbobsausage/Untitled-2.jpg[/IMG]

---

### Post by jken146 on 2008-02-04
From your screenshot, I assume you're string to install Ubuntu on sdb2.  If so, the mount point for this partition should be **/** not /boot.  Also, you won't use more than a gig of swap.

---

### Post by logos34 on 2008-02-04
> **badbob100 said:**
> What HD0-5 do I need to enter for it to install the grub loader onto the 250GB? Why isn't there a drop down box with specfic HD option in GRUB bootloader, like partition manager?

On the 'Ready to Install' screen click 'Advanced' button lower right, then replace '(hd0)' with

> /dev/sdc

--> puts grub bootloader on 250 gb windows drive

---

### Post by badbob100 on 2008-02-06
> /dev/sdc

And now cannot boot off the 250GB in Windows. Great. I can't understand this, it worked last time.

---

### Post by logos34 on 2008-02-06
the ide is probably still confusing the drive designation.  On the windows menu selection press 'e' to edit, 'e' again on the 'root' line and change to (hd0,0).  Then 'enter' and 'b' to boot.

Take out any 'map' commands if present ('O' to edit)

If it works make the change permanent:

gksudo gedit /boot/grub/menu.lst

---

### Post by badbob100 on 2008-02-06
Wiping all partitions and starting again..this time Vista 64 on 250GB, and Ubuntu 64 on a 120GB.

Hopefully work this time...

---

### Post by logos34 on 2008-02-06
seems like a lot of work if the only problem is windows entry in grub won't boot...

---

