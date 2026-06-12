---
title: "Can't find a printer driver"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-05-24
Hi,
I have Ubuntu 7.04 on 32-bit PC. I also have a Lexmark E240n printer and I can't find any printer driver. There is no printer in printer database and there is no driver to download from Lexmark: [http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:554:0:0&searchLang=en](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:554:0:0&searchLang=en)

What should I do to make printer work?
Thanks,
Abcuser

---

### Post by Terl on 2007-05-24
Try LinuxPrinting.org.

Here is a link to your printer:  [Lexmark]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-E240")

---

### Post by abcuser on 2007-05-24
Terl,
I clicked on "Recommended driver: pxlmono" and there is no Lexmark printer drivers available. Any help?
Thanks,
Abcuser

---

### Post by Terl on 2007-05-24
Did you read the top portion, about using the generic driver?  See here, I bolded and italicized relevant parts:

> 

Notes
***Works out of the box on a straight Debian Sarge system with CUPS using the Generic PCL6 driver; the same can be said for Ubuntu "Dapper Drake" and "Edgy Eft" releases of GNU/Linux.***

Lexmark states that this printer is compatible with GNU/Linux systems, however, to get the full functionality of the printer (such as altering configuration options in the printer itself) the proprietary software is required.

The printer can support PCL5 and PCL6 input; it does NOT accept PostScript input. It "supports" PostScript on Mac OS X through a proprietary print filter with a PPD for CUPS that enables printer options to be set. No drop-in replacement for this filter is available for other *nix like systems at this time. The filter is a compiled Universal binary, not a script, so it will not run on FreeBSD, Linux, or any other system that isn't Mac OS X (to my knowledge). 

Discussion forum
Look for help in our forum for printers from Lexmark and IBM.

Miscellaneous
Printer supports PJL.
Printer supports direct text printing with the `us-ascii' charset.
Refill: 1.5K & 2.5K cartridges available from Lexmark with varying terms, conditions, and prices. 6K cartridge available from OfficeSupplyOutfitters.com for about half Lexmark's price, as well.
Known autodetection signatures: USB.

---

### Post by abcuser on 2007-05-24
Hi,
I read this but clicking to "Recommended driver: pxlmono" link: [http://openprinting.org/show_driver.cgi?driver=pxlmono&fromprinter=Lexmark-E240](http://openprinting.org/show_driver.cgi?driver=pxlmono&fromprinter=Lexmark-E240)
in the middle of the web page there is "Select printer" combo box, but there is no Lexmark listed. I am little bit confuged what to select...
Thanks,
Abcuser

---

### Post by Terl on 2007-05-24
Go here:  [Cups]("http://www.cups.org/") and read how to use it.  You should have cups on your pc.  You could also try administration, printing and add a printer that way and select the PCL6 driver.

Did you read the text I pasted?  It says to use Cups.

---

### Post by abcuser on 2007-05-25
Hi,
I have read all your text, but I have never heart about Cups. Why the hack I need to know all this tech staff just to install printer driver? Where is something like setup.exe driver like in Windows??? I can't believe this is so much technical and I must spend few days to study all this tech staff. Is there any three-step tutorial? Any command to execute or something like that?
Thanks,
Abcuser

---

### Post by Terl on 2007-05-25
Have you checked your system menu, administration, printers?  You can add your printer there.  Per the documents you need to use the PCL6 driver.

I understand your frustration with this but many printers are **not** made with Linux in mind.  Printer manufacturers found it cheaper to make printers with less processing ability that rely on windows to "push" them.  As a result the printers are cheaper and many people are then stuck using windows.

You may find that, later if you stick with Linux, you will want to get a printer completely compatible.  Shop around.  HP printers are a good place to start.

As for the tech stuff, sadly, you are learning a new operating system Linux is **not** windows (thank God) so you **will** have to learn things.  If you do not want to learn or you think Linux is all point and click like windows you may be stuck more often than not.  I apologize if my earlier response sounded harsh, but when you are learning a new o/s you have to be willing to learn the "tech stuff".

---

