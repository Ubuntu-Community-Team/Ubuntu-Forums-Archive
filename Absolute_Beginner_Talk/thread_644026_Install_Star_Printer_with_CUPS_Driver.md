---
title: "Install Star Printer with CUPS Driver?"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by sjaguar13 on 2007-12-18
I have a Star Micronics TSP600 printer that I want to use with Ubuntu. The readme file says:
This software requires that the following is present on your computer:

1. CUPS server & architecure (see [www.cups.org](www.cups.org))
2. CUPS development headers (if you choose to re-compile the drivers)
   These files are included in the cups-devel-1.1.19-13.i386.rpm package, which can be obtained at:
   [http://rpmfind.net/linux/rpm2html/search.php?query=cups-devel&submit=Search+...&system=&arch=](http://rpmfind.net/linux/rpm2html/search.php?query=cups-devel&submit=Search+...&system=&arch=)


When I went to cups.org, it said to first check localhost:631 to see if it was already installed. It was. Do I need the development headers? After that, all I am supposed to do is type "make install". When I do that, I get an error.

./setup: 50: Syntax error: Bad substitution
make: *** [install] Error 2

If I want to recompile, I can type "make", but that also gives me an error.

#get ppd options via lphelp
lphelp ppd/sp512.ppd >> docs/sp512-options.txt
/bin/sh: lphelp: not found
make: *** [sp512-options.txt] Error 127

 I really have no idea what I am doing, but this is the first step. The only thing I can think of is I don't have the development headers.

---

### Post by stump138 on 2007-12-18
You should already have CUPS installed.  To verify this/repair try:
```
sudo aptitude update && sudo aptitude reinstall cupsys
```

As far as your printer is concerned: try here:

[http://openprinting.org/printer_list.cgi]("http://openprinting.org/printer_list.cgi")

That has a relatively current list of printers there.

---

### Post by sjaguar13 on 2007-12-19
Does doing that make sure the development headers are installed?

---

### Post by sjaguar13 on 2007-12-20
Never mind. I found out that the drivers are made for RHEL and not Ubuntu. I installed CentOS and they worked fine.

---

