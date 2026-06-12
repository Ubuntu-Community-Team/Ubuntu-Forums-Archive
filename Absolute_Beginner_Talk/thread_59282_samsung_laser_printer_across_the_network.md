---
title: "samsung laser printer across the network?"
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-08-23
How do I print to my samsung ML-1200 laser printer that is connected to my draytek vigor 2600 router?

When I was on windows I had to install the printer but I don't know how to install a printer on linux.

---

### Post by KingBahamut on 2005-08-23
Assuming the Printer is set on your router, I also assume he gets an IP. 

Im assuming you could print to IP via LPR or Cups, granted there is a valid driver for your printer for either. 
 
[http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-1200](http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-1200)

---

### Post by gammyhand on 2005-08-23
Yep, it has an IP address so I shall have a go with that driver. Thanks a lot :)

---

### Post by gammyhand on 2005-08-23
[QUOTE=gammyhand]Yep, it has an IP address so I shall have a go with that driver. Thanks a lot :)[/QUOTE]
 Sod it, that's not working. I have plugged my printer into a USB port on my machine...how do I get it to print something from openoffice for me?

---

### Post by KingBahamut on 2005-08-23
Should be able to add it via your Printers management window within Administration, if its connected via the USB cable. 

or verify that cupsysd is running 

and open up a page to [http://localhost:631](http://localhost:631)

and then administer from there.

---

### Post by gammyhand on 2005-08-23
Thanks :)

---

