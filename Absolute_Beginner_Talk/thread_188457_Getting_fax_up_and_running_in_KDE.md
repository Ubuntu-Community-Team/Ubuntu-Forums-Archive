---
title: "Getting fax up and running in KDE"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by DaBigUA on 2006-06-04
Hello.  I am happily wading into Linux/kubunut/KDE and I need some help with setting up my fax modem to fax.  I see that KDE has faxing "built in" as a pseudo printer, but I can't get it to work.

What steps should I pursue to tell KDE where my fax is and how to use it?  So far, what works is:
[INDENT]CTRL-P from application, 
"Send to Fax" as printer
"Print"
Add fax recipient from addressbook (Kontact).
Click on Send Fax icon
[/INDENT]
KDE responds instantly with error message.  Reading the log reveals:
- - - - -
Converting input files to PostScript

Sending fax to xxxxxxxxx (test (Fax))

Sending to fax using: /usr/bin/fax NAME="'andrew'" DEV='ttyS1' PAGE='letter'  send  'xxxxxxxxxx' '/tmp/kde-andrew/kdeprint_eczAlXQ3' 
/bin/sh: /usr/bin/fax: No such file or directory
- - - - -

Do I need to mount the fax?  Install something? Change something in system settings?

Any advice appreciated, thanks in advance.

---

