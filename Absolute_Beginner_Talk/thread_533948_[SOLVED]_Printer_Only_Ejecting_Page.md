---
title: "[SOLVED] Printer Only Ejecting Page"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by arnold.pietersen on 2007-08-24
I have set up a Lexmark 612.  The printer is detected when I install a New Printer.  However, when I print a page, it is ejected and nothing is printed.

Any help?

Arnold

---

### Post by Daveth on 2007-08-24
is that the Z612? This

[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z612](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z612)

shows that it works" perfectly" under linux. What have you tried printing and from which application?

---

### Post by arnold.pietersen on 2007-08-24
Daveth

Yes it is the Z612 and the printer is now working.  

There are two things I did.  The first was to install the Z600 driver in /usr/share/cups/model so that it appears in the  model list.  The second was to modify /etc/fstab to mount the USB file system.

Thanks for your help.

Arnold

---

### Post by Daveth on 2007-08-25
Hurrah!

---

