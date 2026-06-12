---
title: "Sane-Find-Scanner Help"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Apple 101 on 2006-06-22
Hi all,

I'm trying to use the sane-find-scanner command to detect my scanner, but it appears to be not installed.  XSane is installed though.  Oh, I couldn't find it listed in Synaptic either.

---

### Post by enyaw on 2006-06-22
[QUOTE=Apple 101]Hi all,

I'm trying to use the sane-find-scanner command to detect my scanner, but it appears to be not installed.  XSane is installed though.  Oh, I couldn't find it listed in Synaptic either.[/QUOTE]

Turn All in one printer on // or scanner on and then start Gimp.  Gimp should detect your scanner. :) 

=enyaw

---

### Post by Apple 101 on 2006-06-23
Gimp/XSane didn't detect it.  I tried running as the root user, and also read the man pages.

---

### Post by Apple 101 on 2006-06-23
It is a USB scanner if that makes a difference - which I think it does.  Can I view the USB information detected?  Some time ago, there was a useful programme called usbview that gave information about connected devices.

---

### Post by enyaw on 2006-06-24
[QUOTE=Apple 101]It is a USB scanner if that makes a difference - which I think it does.  Can I view the USB information detected?  Some time ago, there was a useful programme called usbview that gave information about connected devices.[/QUOTE]

Yes I have that USB floppy.  I used it on a Gateway and it reported the Gateway didn't support USB, this was true, so I guess the program works.  I'll look for the floppy perhaps it will tell us where you can find it on the web.  

My hook up is HP PSC-1400v ALL-IN-ONE Printer-Scanner-Copier and it connects to USB 2.0.   If you haven't already, try this:

Turn on scanner
Click Application
Click Graphics
Click Gimp

The Gimp program starts:
Click File
Click Aquire
Click Xsane

A small drop down will appear, and your scanner should show here.  Click on scanner.  "First make some image to be scanned available on the scanner" 

Hope this helps. :)

---

### Post by Apple 101 on 2006-06-24
[QUOTE=enyaw]Turn on scanner
Click Application
Click Graphics
Click Gimp

The Gimp program starts:
Click File
Click Aquire
Click Xsane

A small drop down will appear, and your scanner should show here.  Click on scanner.  "First make some image to be scanned available on the scanner" 

Hope this helps. :)[/QUOTE]Xsane says no scanners were detected.  I tried the help suggestions provided too.  My scanner is most likely not supported.  I'll try using Wine to run the software...

---

### Post by Sef on 2006-06-24
> I'm trying to use the sane-find-scanner command to detect my scanner, but it appears to be not installed. XSane is installed though. Oh, I couldn't find it listed in Synaptic either.

It sounds like your software did not install correctly.   Applications > Graphics > Xsane Image Scanner (if you got Ubuntu) and you should be able to scan.  

What version of Ubuntu do you have? And is it Dapper?

---

### Post by Apple 101 on 2006-06-24
Ubuntu 6.06 (Dapper Drake).  I cannot use *sane-find-scanner* or *scanimage -L* because the terminal says the command do not exist (or whatever that message is).

Should I remove Xsane, and reinstall it?

---

### Post by Sef on 2006-06-24
try this from the terminal:

sudo apt-get update

sudo apt-get install ubuntu-base ubuntu-desktop

sudo apt-get dist-upgrade


hopefully that will install any missing software for you.  It did for me.

---

### Post by Apple 101 on 2006-06-24
I'll try it and see.

---

### Post by Sef on 2006-06-24
Report back if it works or not.  Thank you.

---

### Post by Apple 101 on 2006-06-24
All of the packages are up-to-date.  The commands still aren't working.  Thankyou for trying though.

---

### Post by Apple 101 on 2006-06-25
I checked the Universe repository, the packages sane and sane-utils were not installed.  Why were they in Universe though?  I thought they were stable builds.

Anyway, now sane-find-scanner and scanimage -L work, except that my scanner is not supported and not detected from the kernel, only by libusb.

Thankyou everyone for all of your effort with this issue.

---

### Post by enyaw on 2006-06-26
[QUOTE=Apple 101]I checked the Universe repository, the packages sane and sane-utils were not installed.  Why were they in Universe though?  I thought they were stable builds.

Anyway, now sane-find-scanner and scanimage -L work, except that my scanner is not supported and not detected from the kernel, only by libusb.

Thankyou everyone for all of your effort with this issue.[/QUOTE]

Tell us the manufacturer of the scanner.:-k 

Thx enyaw

---

### Post by Apple 101 on 2006-06-27
Canon Canoscan 3000F
[QUOTE="Sane-Find-Scanner"]
found USB scanner (vendor=0x04a9 [Canon], product=0x2215 [CanoScan]) at libusb:002:002[/QUOTE]

---

### Post by Ernest Pons-Worley on 2006-06-27
I'm having the same problem.  I know my scanner is supported because it worked with Hoary Hedgehog and with Breezy Badger.  In the past I had turned the scanner on when installing Ubuntu and Xsane was configured automatically during the install.  I made the mistake of not turning the scanner on when I upgraded to Dapper Drake, so now it doesn't see the scanner.  I'm getting the same Xsane message: "no devices found."  The update suggested just says that "ubuntu-base is already the newest version."

Does anyone know how to configure the Xsane backend manually?

Thanks,
Ernest

---

### Post by Apple 101 on 2006-06-27
My scanner can't be turned on as such.  It is always on, ready to be used when you select the Acquire command (in Windows, anyway).

---

### Post by chunk on 2006-07-07
Same problem here (although my scanner is Epson CX4200 all-in-one). Supposedly sane-find-scanner does the trick, but I'm hesitant to install it now that it has been moved to universe. Why has sane-utils been moved to universe?

---

### Post by Apple 101 on 2006-07-08
> **chunk said:**
> Same problem here (although my scanner is Epson CX4200 all-in-one). Supposedly sane-find-scanner does the trick, but I'm hesitant to install it now that it has been moved to universe. Why has sane-utils been moved to universe?I'd like to know that too, but I installed both the *sane* and *sane-utils* packages from Universe, and nothing has gone wrong at all.  Enable the Universe repository, reload, and search for *sane*.

---

