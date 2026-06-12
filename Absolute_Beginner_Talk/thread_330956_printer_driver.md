---
title: "printer driver?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by thaKing on 2007-01-03
i have a Dell laser 1100 printer...when i added the printer it was recognized immediately, however i suspect the driver has not been installed...when i try to print nothing happens...how do i make sure the driver is installed properly?

---

### Post by Efwis on 2007-01-03
dell printers are rebranded Lexmark printers. 
And typical of Dell, they don't offer support for this printer in Linux.

currently I would suggest getting a different printer if you can.

---

### Post by thaKing on 2007-01-03
not gonna do that...it's barely a year old and i'm just using ubuntu to try and learn linux...i guess i'll do without...

thanks

---

### Post by Hendrixski on 2007-01-03
There are usually some close approximations.  I don't know how you went around installing the printer but try typing this into your browser.   localhost:631   It connects you to the printer port, and gives you web-based administrative tools so that you can try any number of drivers (and they give you a list with several hundred thousand) if one doesn't work try another.  it will auto direct you to the one that best suits your need.

---

### Post by thaKing on 2007-01-03
off the top of my head (i'm not sitting in front of the machine at this time so i may be a little off in my explanation) i selected System>Administration>Printing and clicked on New Printer...it detected my printer (i'm assuming so because it gave it the correct name)...

---

### Post by Hendrixski on 2007-01-03
> **thaKing said:**
> off the top of my head (i'm not sitting in front of the machine at this time so i may be a little off in my explanation) i selected System>Administration>Printing and clicked on New Printer...it detected my printer (i'm assuming so because it gave it the correct name)...

Yeah, honestly , I've never done it that way.  A long time ago I've installed printers from the Command line on Solaris UNIX... now I just use the web interface.  [http://localhost:631](http://localhost:631), then under the tab for administration it'll show you all the printers it detects connected to your computer, or even on the network (You may be amazed how many printers you have access to... if you're in an office then you'll be able to access coworkers private printers that they didn't recall sharing under Windows).  Just click install next to that printer, it highlights the best driver by default so just click OK.  If it doesn't work, it shows you other drivers that would work as well.

It takes 2 minutes to install a printer in this fashion.

---

### Post by Hendrixski on 2007-01-03
Oh yeah, sometimes you may have a printer hooked up to a Windows machine that you can 'install' in your Linux box, but you may need to install software on the Windows machine that allows any other OS to print to it (because it's on the install CD, but it's a separate option that almost nobody choses to install).

---

### Post by slarty72 on 2007-01-05
I've got this printer as well and have finally got it working using the Samsung ML-1610 Foomatic/gdi driver on edgy.

Printed a lovely test page (at last!)  first time

---

