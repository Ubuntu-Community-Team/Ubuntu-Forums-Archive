---
title: "USB Printer CUPS Setup"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by rgeddes on 2006-10-21
I'm trying to get my USB printer to work.  I'm using CUPS to setup the printer.

CUPS, in the "Where do I begin" section says:

"If you have a printer connected to a USB or parallel port, you will see it listed as a new printer" in the Administration section...

I see 4 entries in the "New Printers Found" section:
- Canon i560 (Canon i560 USB #1)
- CANON (Parallel Port #1)
- EPSON (Parallel Port #1)
- Canon i560 (USB Printer #1 with status readback for Canon BJ) 

I have only "1" printer (Canon i560) connected to my USB port.

I assume that the hardware device (as in lspci, lsusb) has been mapped to a file in the /dev/ directory, and that is where CUPS is reading the incorrect list of printers connected to my computer.  

I tried adding both entries that refer to Canon i560/USB.  Neither printed the test page, and the one with "readback" said it could not find the file /dev/usblp0.  I checked and it does exist.

If anyone has a "quick" fix for getting my printer running, I'd be interested.

Better yet, does anyone know of a way to tell which  hardware devices are mapped to which files in the /dev/ directory.  A utility like lspci or lsusb that lists the associated file in the /dev/ directory would be nice. 

Thanks

---

### Post by localuser on 2006-10-22
Try going to [http://localhost:631/](http://localhost:631/) and seeing if that helps.

---

### Post by Saphira on 2006-10-22
You could also try searching here>>  [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

---

### Post by gn2 on 2006-10-22
You could also sell it on eBay and get an HP printer instead?

---

### Post by rgeddes on 2006-10-22
- I forgot to mention I am using localhost:631... that is the application that's giving me the bogus info about having 4 printers connected.

- Interesting website [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page) lots of info there... some minor annoyances like when describing an install procedures old packages are mentioned... libtiff3g, instead of the current package libtiff4... took me a while to figure out I already had it installed

- Sounds like the lad/lass has an aversion to my printer.. does this printer have a bad reputation in Linux...? In Windows, I think it's a better printer than the HP's.

Thanks for the replies

---

### Post by gn2 on 2006-10-22
Don't know anything about your printer specifically, but HP are generally the best supported in Linux.

Was intended as a humorous yet serious suggestion.

---

### Post by ReaderRat on 2006-10-22
> Sounds like the lad/lass has an aversion to my printer.. does this printer have a bad reputation in Linux...? 

Check it in the [Hardware Compatibility List](http://www.linux-drivers.org/)

---

