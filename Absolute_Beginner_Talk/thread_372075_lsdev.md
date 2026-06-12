---
title: "lsdev"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by benphane on 2007-02-27
From readings, such as at [http://www.linuxcommand.org/man_pages/lsdev8.html]("http://www.linuxcommand.org/man_pages/lsdev8.html")
 , I get the impression that the lsdev command could be useful.

Googling does not help me figure out why "lsdev" returns "command not found."

It appears that lsdev is not available under Ubuntu.

Running 6.10.  Originally installed with Gnome.  Switched to KDE.

Any knowledge regarding lsdev specifically or, learning linux commands in general, greatly appreciated.

---

### Post by Brunellus on 2007-02-27
the ones you might be interested in:

lspci (lists devices on the PCI bus)
lsusb (ditto for USB)

running them with -v flags will increase output verbosity.  lspci -vvv will be very very detailed.

---

### Post by benphane on 2007-02-27
Hello Brunellus,

lspci -vvv is most certainly verbose -- full of very useful information.

Thank you very much.

Do you have a "lsdev" command in your environment?

---

