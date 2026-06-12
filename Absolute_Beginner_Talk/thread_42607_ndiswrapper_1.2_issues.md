---
title: "ndiswrapper 1.2 issues"
date: 2005-06-18
forum: Absolute Beginner Talk
---

### Post by cvogel on 2005-06-18
Hi all.  I'm running and AMD64 installation of Kubuntu and I wanted to get my wireless working through ndiswrapper.. I know there has been plenty of threads on this situation but I have encountered something I seem to be unable to find the solution for. I've compiled and installed module 1.2.

I was told in a thread to get the drivers from this area here--

[http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)

I'm using a DWLG520(rev B) card, which is supposed to work.  So, I went ahead and installed the downloaded drivers in ndiswrapper:

sudo ndiswrapper -i NetA3AB.inf

Now, when I try to checked the driver list I got this:

sudo ndiswrapper -l 
neta3ab        invalid driver!

I have two network adapters--the DWLG520 and a Linksys WUSB54G one as well, which is supposed to work flawlessly.

I've tried the drivers for the WUSB54G adapter(which ndiswrapper was written for) and I get the same problems, with all drivers.  The ones on CDs don't work either.

Is this a 64 bit problem?

---

### Post by poofyhairguy on 2005-06-18
[QUOTE=cvogel]
Is this a 64 bit problem?[/QUOTE]

Probably. Those *.inf files were compiled for 32bit windows....

---

