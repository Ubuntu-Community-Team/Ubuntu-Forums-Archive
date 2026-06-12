---
title: "Can't print a page(Gutsy, CUPS)"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by BeholdMyGlory on 2008-04-12
When I'm trying to print a web page from Firefox, using CUPS with my HP PSC 500, it results in my printer printing some wierd pages. The first page is the first maybe... tre centimeters of the web pge, then white. Next page is just some weird black lines all over the page, then i get the next three centimeters of the page, and the page after that is just more black lines...
Well. I've managed to print both a document and a web page from WinXP, so it's not a problem with the printer, but my guess is that it would be CUPS or the drivers that CUPS is using.
Any ideas?

---

### Post by djbsteart1 on 2008-04-12
Use HPLIP if you are not already, it was designed by HP for Linux and can handle most printers. I think it is installed by default, it handles my HP without any problems.

---

### Post by LowSky on 2008-04-12
clcik on this link

[http://localhost:631/]("http://localhost:631/")


it will help you set up your printer

---

### Post by BeholdMyGlory on 2008-04-13
> **djbsteart1 said:**
> Use HPLIP if you are not already, it was designed by HP for Linux and can handle most printers. I think it is installed by default, it handles my HP without any problems.

Yes, apparently I do have a package installed called hplip, not really sure what it does or how to set it up though... is it a replacement for cups? Or a driver? Sorry, I don't know much about these things.

> **LowSky said:**
> clcik on this link

[http://localhost:631/]("http://localhost:631/")


it will help you set up your printer

Hm... Don't know what to change there.

Also, it's strange, but i can print a test page just fine, but when printing from FF or OOo, well... the printer gets really strange. It also seems to respond much slower.

I do recall updating cups or libcups from the repositories shortly before it started happening, but I don't know if it started happening right away, or if I managed to print something afterwards.

---

### Post by crf on 2008-04-13
Does it only happen if you print from firefox and Ooo?
Firefox also has an option to print to a file, and to print to pdf. You can see if those result in different output. (At least, for me, using firefox 3 and hardy.)

You can change the driver used by your printer, or make sure it is the right one, by using system menu --> administration --> printing , which will open system-config-printer, and then changing or verifying the make and model.

---

### Post by BeholdMyGlory on 2008-04-14
> Does it only happen if you print from firefox and Ooo?
Firefox also has an option to print to a file, and to print to pdf. You can see if those result in different output. (At least, for me, using firefox 3 and hardy.)

No... It's the same from other applications as well (at least KPDF). And the output seems correct when printing to PDF. But I can't print the PDF-file, it results in the same half pages and weird black lines.

> You can change the driver used by your printer, or make sure it is the right one, by using system menu --> administration --> printing , which will open system-config-printer, and then changing or verifying the make and model.

That menu doesn't apply to me using kde ;) but I get what you mean, and I'm using the recommended driver (a driver that apparently was released by HP as open source).

---

### Post by djbsteart1 on 2008-04-15
Hplip will set up your printer for you, if you open it, then follow the instructions through. So if your printer is usb select usb, network select network.....
Then, the printers ppd file should be auto selected, but there is a chance you will have to get it from linuxprinting.org. Otherwise this is a really good piece of software.

---

