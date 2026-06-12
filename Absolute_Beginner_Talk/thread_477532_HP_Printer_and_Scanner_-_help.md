---
title: "HP Printer and Scanner - help"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by mjp29 on 2007-06-18
We have teh HP Business inkjet 1200d printer and the HP Scanjet 5550c scanner.

How do we get these specific peripherals to work in Ubuntu

---

### Post by steve.horsley on 2007-06-19
For the printer, connect it and turn it on, then go:
System->Administration->Printing,
Add printer...
It should find the printer so all you do is yes, yes, yes.
When you get to a page that names a recommended dtiver ande a button to install a driver, don't be tempted/fooled by the add driver button - just go witht eh recommended driver (that's already installed). The add driver button is a trap and will have you needlessly searching for hours.

---

### Post by p_quarles on 2007-06-19
I second steve.horsley's advice. I'd just add that Ubuntu has great built-in support for HP printers and scanners. Once you get the driver setup, configure the HPLIP toolbox. This will add a lot of functionality, including ink-level monitoring if supported by the printer.

---

### Post by wpshooter on 2007-06-19
> **steve.horsley said:**
> For the printer, connect it and turn it on, then go:
System->Administration->Printing,
Add printer...
It should find the printer so all you do is yes, yes, yes.
When you get to a page that names a recommended dtiver ande a button to install a driver, don't be tempted/fooled by the add driver button - just go witht eh recommended driver (that's already installed). The add driver button is a trap and will have you needlessly searching for hours.

I somewhat disagree with the "recommended driver" advice.  You may want to try several from the list for your printer.  The recommended one does not always work the best and sometimes not at all.

Good luck.

---

### Post by maverick78 on 2007-06-19
I might also recommend you check out this link for the Linux Foundation's guide for printing: 

[http://tinyurl.com/386zs5](http://tinyurl.com/386zs5) 

In my limited experience there is good support for almost all HP brand printers.

---

### Post by mjp29 on 2007-06-20
We have the hp business inkjet 1200 series printer.

How do we force ubuntu to recognize it?

---

### Post by lamalex on 2007-06-20
did you go to system > administration > printing and add it there?

---

### Post by mjp29 on 2007-07-24
We did successfully install Ubuntu on my Uncles desktop.  We also were successful in having Ubuntu make the printer print.  I think Ubuntu used a generic driver.

However, the printer use to print on both sides of the paper under Windows.  Now the printer only prints on one side of the paper.

If there is a more exact printer driver for his printer that might make it print on both sides of the paper we would like to install such a driver.

His printer is the HP Business Inkjet 1200d

---

### Post by wjp.reg on 2007-07-24
so you checked the properties of the printer to see if two-sided printing was selected?

---

### Post by mlentink on 2007-07-24
You may want to look [here]("http://hplip.sourceforge.net/supported_devices/inkjet.html")

---

### Post by ReaderRat on 2007-07-24
[http://openprinting.org/show_printer.cgi?recnum=HP-Business_Inkjet_1200](http://openprinting.org/show_printer.cgi?recnum=HP-Business_Inkjet_1200)

---

