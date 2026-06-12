---
title: "Hud-Lite"
date: 2007-06-09
forum: Apple Intel Users
---

### Post by dareofficer on 2007-06-09
Hello, could someone assist with installing Hud-Lite?  I can't get it to install.

---

### Post by ronocdh on 2007-06-09
> **dareofficer said:**
> Hello, could someone assist with installing Hud-Lite?  I can't get it to install.
I'm sorry, this isn't nearly enough information for anyone to help you. What trouble have you had, doing what, exactly? Give us hardware and OS information, too.

---

### Post by dareofficer on 2007-06-09
[http://www.hudlite.org/](http://www.hudlite.org/)

Software for download is there.  This program is used to monitor Asterisk, / Trixbox.

It is in a Tar format, and I can't get it to install.

---

### Post by ivesjd on 2007-06-10
When I went to download it it told me its a .rpm not a tar file.

---

### Post by thestef on 2008-01-29
Download the RPM, 

Open a terminal and: sudo apt-get install rpm

unpack the RPM file and copy the content of the usr dir to /usr (i used mc for this)

and just start /usr/fonality/hud-lite/start_HUD.sh 

i made a starter for it and put the command into the session manager.

---

### Post by cyberdork33 on 2008-01-29
You should convert the rpm to a deb file for use in the Ubuntu package manger.
```
sudo apt-get install alien
sudo alien /path/to/file.rpm
```

---

### Post by ganjuror on 2008-03-22
alien fails on this RPM - others have supposedly had success with cpio to extract the files from RPM and then just running the launch script, or by   installing the RPM package and doing rpm-i --nodeps hudlite...rpm.  Installing the RPM failed for me with:

error: can't create transaction lock on /var/lib/rpm/__db.000

And extracting the RPM allowed me to actually RUN the client, which connects to the server and sees all the existing extensions, but won't _work_ (no user status, no click-to-call) etc...

See the trixbox forums for more

rpm extraction method:
[http://www.trixbox.org/forums/trixbox-pro/hudlite-hud-pro-trixbox-pro/hudlite-client-ubuntu](http://www.trixbox.org/forums/trixbox-pro/hudlite-hud-pro-trixbox-pro/hudlite-client-ubuntu)

rpm install method:
[http://www.trixbox.org/forums/vendor-moderated-forums/hudlite-trixbox-ce/install-hudlite-ubuntu:](http://www.trixbox.org/forums/vendor-moderated-forums/hudlite-trixbox-ce/install-hudlite-ubuntu:)

---

