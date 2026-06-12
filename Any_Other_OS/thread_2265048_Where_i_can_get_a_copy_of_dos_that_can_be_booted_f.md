---
title: "Where i can get a copy of dos that can be booted from a pen drive/USB?"
date: 2015-02-12
forum: Any Other OS
---

### Post by NunoLava1998 on 2015-02-12
Hello, i have a 2 GB pen drive and i wanted to put a copy of dos of it that is bootable so i can make a iso of it to then customize my own contents.
Also, will it be working fully if i just put batch files there and then boot from the usb to get there? And where would be the name of the batch file so i dont get a "Operating System not found" or a blinking underscore. 


Any help?

---

### Post by lisati on 2015-02-12
Are you referring to a flavour of Ubuntu or something similar to MS-DOS?

You can get an MS-DOS workalike at [http://www.freedos.org/download/](http://www.freedos.org/download/) :D

---

### Post by Lars Noodén on 2015-02-12
Specifically the details of making a USB stick with FreeDOS are on this page:
[http://www.freedos.org/wiki/index.php/USB](http://www.freedos.org/wiki/index.php/USB)

---

### Post by buzzingrobot on 2015-02-12
> **NunoLava1998 said:**
> Hello, i have a 2 GB pen drive and i wanted to put a copy of dos of it that is bootable...

MS-DOS and PC-DOS (the IBM version) are still licensed by Microsoft and IBM.  The only way to get legitimate copies is buy them. (Obviously, DOS hasn't been available for retail purchasing for years.  I *think* it's available through certain development channels and for embedded use.  Both are impractical for your purposes. As suggested, use FreeDOS, an open workalike.

> Also, will it be working fully if i just put batch files there and then boot from the usb to get there? And where would be the name of the batch file so i dont get a "Operating System not found" or a blinking underscore. 


DOS will automatically run an 'autoexec.bat' file on boot, if it is present. A 'config.sys' file can contain device drivers invocations, etc., that will also be executed on boot.

Other batch files, or any other executable, can be launched after boot, of course, or via autoexec.bat.

The traditional DOS interface is a prompt and a cursor.  If a cursor is all you see, it's working.

---

