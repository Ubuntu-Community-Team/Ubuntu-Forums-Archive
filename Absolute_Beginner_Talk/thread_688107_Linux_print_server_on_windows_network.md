---
title: "Linux print server on windows network?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by SuperT on 2008-02-05
I have an old computer without an OS which i would like to use as a print server. If i install ubuntu on it will i be able to use it as a print server if all the other computers on the network are windows?

---

### Post by .nedberg on 2008-02-05
Yes!

It is generally no problem if the printer is recognised (and it generally is). Connect the printer, configure it as shared, install the windows driver on the windows machine and connect to the printer.

---

### Post by nemilar on 2008-02-05
The above post is correct.  Check to see if your printer is supported at [http://www.linuxprinting.org]("http://www.linuxprinting.org")  If it is, setup the printer in Ubuntu as shared.  You can share printers over Samba for Windows machines to access.  The windows machines will need the driver installed, too, however.

---

