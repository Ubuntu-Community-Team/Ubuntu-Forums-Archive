---
title: "Printer Problems"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by jezster on 2007-06-06
Hi All,

Well I have at last managed to dump my XP OS and reformatted the drive as /home.  All is good with the Linux system and I'm a total convert, but I still have one problem to fix.

I have a Lexmark L708 printer connected to my system via USB and I can not make it print, does anyone know how to fix these issues?  It worked perfectly under Windows, but with Linux it doesn't do anything.

I have searched the forum but with no luck... any information would be useful.

Kind Regards

Jezster

Ubuntu 7.04 up-to-date
AMD 3200
1GIG
Nvidia GFX

---

### Post by p_quarles on 2007-06-06
I don't have any experience with Lexmark, but this might help:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

---

### Post by dstew on 2007-06-06
I think you mean Lexmark Z708, correct?

Lexmark does not make a Linux driver for this printer. The [foomatic web site]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z730") says that the Postscript driver works with other Lexmark printers of the Z700 series, although the Z708 is not specifically mentioned. I recommend that you try it with the Postsript driver first. After that, you can try the linux driver mentioned by p_quarles, but I tried the link on that page and it just went to the Lexmark site, and they do not put out that driver any more. You can get the old lexmark driver [Here]("http://users.cybercity.dk/~dko12479/") but if you are a new Linux user, it will be very hard to get it installed properly. You will need to use the Alien program to convert the .rpm to .deb for Ubuntu as it says on that site. If you want to do this, we can help you.

---

