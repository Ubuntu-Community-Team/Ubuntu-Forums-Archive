---
title: "Brother MFC-210C PPD file."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by thenixedreport on 2007-06-19
Does anybody have the PPD file for a Brother MFC-210C printer/scanner/copier on their computer?  If you do, would you be willing to share it so that others can add that specific model to the printer list when installing a new printer.

---

### Post by chimmu on 2007-11-04
> **thenixedreport said:**
> Does anybody have the PPD file for a Brother MFC-210C printer/scanner/copier on their computer?  If you do, would you be willing to share it so that others can add that specific model to the printer list when installing a new printer.

I had the same problem getting my 640-CW working with Gutsy...followed the directions on the brother website and it worked!


1. got the drivers from there (210c)
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de)

2. Modify the package
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#110](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#110)

2-1.Unpack the package
dpkg --unpack cupswrapperXXXX.x.x.x-x.dpkg
2-2.Open /usr/local/Brother/cupswrapper/cupswrapperXXXXX to edit.
2-3.Look for the line with "lpadmin -p XXXXXX -E -v .......".
2-4.Change "-m" to "-P" in the line
2-5.Add the file-path of the PPD file written in the line.
the file path = "/usr/share/cups/model/"

Example
BEFORE(no wrap):
lpadmin -p MFC9420CN -E -v usb:/dev/usb/lp0 -m brmfc9420cn.ppd
AFTER(no wrap):
lpadmin -p MFC9420CN -E -v usb:/dev/usb/lp0 -P /usr/share/cups/model/brmfc9420cn.ppd

---

