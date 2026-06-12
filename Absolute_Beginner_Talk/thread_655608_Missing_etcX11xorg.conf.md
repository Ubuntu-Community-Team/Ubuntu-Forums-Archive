---
title: "Missing /etc/X11/xorg.conf"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by microcronz on 2008-01-01
ello All.  I just reloaded 7.10 Gutsy Gibbon and tried to do the walkthrough to install my video card.  It is a Radeon x1600 pro.  I do the option.  Method 1: Install the Driver the Ubuntu Way and everything works well. When i configure the driver my xorge.conf file is now missing.  It is blank that is.  Is there a way to reload it so i can configure the driver manually.

Here is the walkthrough I used. [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Installation]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Installation")

---

### Post by riven0 on 2008-01-01
Very weird. I don't understand how the xserver could be running if the xorg.conf file is blank. In either case, you may want to open the terminal and do a: **dpkg-reconfigure xserver-xorg**

Then maybe try following the tutorial again.

---

### Post by overdrank on 2008-01-01
> **microcronz said:**
> ello All.  I just reloaded 7.10 Gutsy Gibbon and tried to do the walkthrough to install my video card.  It is a Radeon x1600 pro.  I do the option.  Method 1: Install the Driver the Ubuntu Way and everything works well. When i configure the driver my xorge.conf file is now missing.  It is blank that is.  Is there a way to reload it so i can configure the driver manually.

Here is the walkthrough I used. [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Installation]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Installation")

HI and make sure you type the command correct or just copy and paste ```
gksudo gedit /etc/X11/xorg.conf
``` not xorge.conf

---

### Post by microcronz on 2008-01-01
I get this error while trying to reconfigure the x-server.

```
/usr/sbin/dpkg-reconfigure must be run as root

```


Also I just loaded Envy and tried to load the ATI drivers.  Said it worked.  Rebooted and still no file.  Just the blank page. And flgrxinfo says all messa info.

---

### Post by dr.silly on 2008-01-01
sudo dpkg-reconfigure xserver-xorg

---

### Post by gmjs on 2008-01-01
You must run **dpkg** as a user with root privileges.

Use **sudo** before the rest of the command and enter **your** password when prompted.

**# sudo dpkg-reconfigure xserver-xorg**

You should be able to accept all the default values at each dialogue, although I would recommend choosing **Medium** and ** NOT Advanced** when choosing a screen resolution.

---

### Post by dr.silly on 2008-01-01
sudo - superman user superduper power user do

---

### Post by microcronz on 2008-01-01
Will that reload my /etc/X11/xorg.conf file.   When I open that to configure the driver it is blank.

---

### Post by dr.silly on 2008-01-01
it should create a new /etc/X11/xorg.conf for you

---

