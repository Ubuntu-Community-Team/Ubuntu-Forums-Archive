---
title: "Linux Drivers for Canon iP1700?"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-05-26
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

This seems like it will work, but it costs $39.  Is there a way to simply get a driver for this printer?  I looked on Canon's website and they don't list any Linux drivers.

---

### Post by userundefine on 2007-05-27
No, that's rubbish.  Don't pay for that.

Printer works perfectly with the driver listed [here]("http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1700").

---

### Post by kc5hwb on 2007-05-28
I got that driver, but it is an RPM package, how do you install RPMS in Ubuntu?  I haven't done rpms since my Mandrake 8.1 days, using Webmin.

---

### Post by userundefine on 2007-05-28
Install alien with apt-get.  Then use alien *.rpm file*.  It usually works.

If not, I'm sure the driver is accessible via apt or is already installed.

---

### Post by kc5hwb on 2007-05-30
Alien successfully converted the files into a .DEB file and I was able to install it.  But I don't know where it put it and when I try to install the printer, the ip2200 still doesn't show up in the drivers database.  I try a "Use Disc" but I cannot find the .pdd file it wants to install.

---

### Post by userundefine on 2007-05-31
Check /usr/share/cups/model/canonip2200.ppd

---

### Post by sjh874 on 2007-06-04
It installs just fine with the changes to the maxmediaW&H, it's just that when it shows up in the printers it's paused. when i resume it and try a test print the jobs all say stopped. any idea what could fix that.

---

### Post by kcid2829 on 2007-07-13
I'm a newbie to Linux.  Can't install the Turboprint driver for Canon iP1700.  Can someone tell me the exact steps?  I have it on a CD.

---

