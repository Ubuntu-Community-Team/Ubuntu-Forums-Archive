---
title: "How can I use this printer w/ ubuntu linux?"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by JReagan1990 on 2006-11-27
How can I use the canon mp160 printer with ubuntu?

---

### Post by duality on 2006-11-27
[http://forum.ubuntu.cz/viewtopic.php?id=4770](http://forum.ubuntu.cz/viewtopic.php?id=4770)

(the form is in another language but see the links posted there)

Canon has verry poor Linux support, and it might be hard to set the Canon printers up with Linux =/, but GL

---

### Post by pelo8280 on 2007-04-07
Download this: [ftp://rpmfind.net/linux/fedora/extras/development/i386/gutenprint-5.0.0.99.1-2.fc7.i386.rpm]("ftp://rpmfind.net/linux/fedora/extras/development/i386/gutenprint-5.0.0.99.1-2.fc7.i386.rpm")  to your desktop.  Install "Alien" through the Synaptics Package Manager (it may already be installed).  Open a terminal window and type:
     sudo alien --scripts [*path to rpm file*]
This will create a deb package in your home folder (or the folder that you cd'd to).  Run and install that.  Then, attach your printer, turn it on, Go to System, Administration, Printing, add, etc. and install the printer with the "MULTIPASS MP150" driver.

Your Canon Pixma MP160 should work.

---

