---
title: "GUI for editing GRUB"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by harisund on 2006-03-24
Simple. Is there a GUI application for editing Grub? 

Such as
.)Change time out for operating systems. 
.)Change order of operating systems. 
.)Change command line options while booting, and ability to choose a kernel to boot. 

I know, I can edit the /boot/grub/menu.lst , but still.. I believe people will be better off with a GUI. 

Thanks !

---

### Post by pbaehr on 2006-03-24
There is this:
[http://grubconf.sourceforge.net/](http://grubconf.sourceforge.net/)

---

### Post by harisund on 2006-03-24
Ah ! Thank you very much.

---

### Post by pbaehr on 2006-03-24
No problem. Can't vouch for it, though. I don't use it, I just found it through google.

---

### Post by aysiu on 2006-03-24
[QUOTE=pbaehr]There is this:
[http://grubconf.sourceforge.net/](http://grubconf.sourceforge.net/)[/QUOTE] That project's retired, but it pointed to another project called Gnome System Tools.

Apparently, there's no official support for Ubuntu yet:
[http://www.gnome.org/projects/gst/distros.php](http://www.gnome.org/projects/gst/distros.php)

And you'd have to compile it yourself anyway:
[ftp://ftp.gnome.org/pub/GNOME/sources/gnome-system-tools/2.14/](ftp://ftp.gnome.org/pub/GNOME/sources/gnome-system-tools/2.14/)

That's not terribly practical. It's a lot easier to change one or two things in a configuration file than to compile from source.

---

