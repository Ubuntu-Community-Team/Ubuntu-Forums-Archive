---
title: "[SOLVED] CUPS does not print anymore"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-10-09
It must have happened after some upgrade, I get the Printer box, says 'printing' but does
not print anymore to hp5160.

Works from Windows.

Please help.

---

### Post by gautada on 2007-10-09
Your printer seems fully [supported]("http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_5160").  Just reinstall.  Unless the printer is working and you are having application trouble.

---

### Post by dptxp on 2007-10-09
> **gautada said:**
> Your printer seems fully [supported]("http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_5160").  Just uninstall and reinstall.

Yes, it used to print.
Unistall and install what ?

---

### Post by dptxp on 2007-10-09
Tried to remove CUPS from Synaptic. Too many files. Did not know which to remove and
reinstall.:confused:

---

### Post by aconley1 on 2007-10-09
Don't uninstall CUPS....go into your printer manager under System / Administration / Printing and remove the printer that is not working and then re-install it.

---

### Post by gautada on 2007-10-09
Don't forget to use [hpijs]("http://packages.ubuntu.com/feisty/text/hpijs").

---

### Post by dptxp on 2007-10-09
> **aconley1 said:**
> Don't uninstall CUPS....go into your printer manager under System / Administration / Printing and remove the printer that is not working and then re-install it.

Thanks

> **gautada said:**
> Don't forget to use [hpijs]("http://packages.ubuntu.com/feisty/text/hpijs").

Had removed it using add/remove. Added it using add/remove but cannot find the ODD file.

---

### Post by gautada on 2007-10-10
What do you mean by ODD file?

---

### Post by philinux on 2007-10-10
When you say it does not print are there any error messages?

---

### Post by dptxp on 2007-10-10
> **gautada said:**
> What do you mean by ODD file?

Sorry, .ppd file.

I installed from the website, put in the .ppd driver too, it printed a page or two (damn slow),
now it does not print again (says 'printing'.....)

My system seems have slowed down, it has 256 MB RAM. The printer dialog boxes are very slow.

---

### Post by dptxp on 2007-10-10
> **philinux said:**
> When you say it does not print are there any error messages?

No, says 'printing', I checked driver, says installed (right one).

---

### Post by philinux on 2007-10-10
you may need to reboot with the printer switched on.

---

### Post by por100pre1 on 2007-10-10
Try setting CUPS from this address: [http://localhost:631/admin](http://localhost:631/admin)

---

### Post by dptxp on 2007-10-10
> **por100pre1 said:**
> Try setting CUPS from this address: [http://localhost:631/admin](http://localhost:631/admin)

Says ' job not complete' when I click there to reprint.
Does not print.

Administration Page says 4 printers found.
2 hp5100
1 Canon on P.Port
1 Epson on P.Port.

I have a HP5160 on usb (correctly displayed in Printers page of localhost:631

---

### Post by por100pre1 on 2007-10-10
Try using HPLIP toolbox and verify that the printer is IDLE and Accepting Jobs under the Status Tab. Reject any jobs and try again. :-k

---

### Post by gautada on 2007-10-11
> **dptxp said:**
> I installed from the website

What website???  The website I quoted was for information only.  Uninstall that and go with System->Administration->Synaptic Package Manager.  Reinstall CUPS (without uninstalling) and make sure you have hpijs installed as well.  Sorry I was not more clear.

---

### Post by gautada on 2007-10-11
I gnore my last post.  I didn't read the entire thread.

> **dptxp said:**
> My system seems have slowed down, it has 256 MB RAM. The printer dialog boxes are very slow.

This is probably why things are so slow.

---

### Post by dptxp on 2007-10-11
> **gautada said:**
> I gnore my last post.  I didn't read the entire thread.



This is probably why things are so slow.

It had 256MB RAM from day 1 and I have been running Ubuntu on it for months now.
I know that 256 MB RAM is low, but I do not open too many applications at the same
time, and I also have checked system monitor a few times.

Browsing is not slow, but recently the machine has slowed down.

---

### Post by dptxp on 2007-10-11
It is working now.
I had to change the connection from 'NETWORK' to 'LOCAL' in printer
properties.

Thanks to all.

---

