---
title: "CUPS positive laserprinter experience on ubuntu feisty desktop?"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by ronny_d on 2007-07-30
Who has an immediate good experience with CUPS on Feisty Fawn 7.04 desktop (!) version and what was the laserprinter (no inktjet) and how about the connection (like parallel or usb or...) and how are all programs (pdf, OpenOffice, texteditor, gimp, what more, all of them) printing for you? So who can inform me positively on a laserprinter configured in CUPS succesfully without hassle on Feisty Fawn 7.04 desktop (!) and what about the connection. Please especially your personal positive experiences, name / specificiation of the laserprinter, way of connection (parallel of usb or both) and whether CUPS did such from 'system' and in administration 'printers' or whether you had to use the browser localhost 631 and so on, with or without hassel and whether you already printed succesfully from all programs i mentioned. Thanks... *

---

### Post by stchman on 2007-07-30
> **ronny_d said:**
> Who has an immediate good experience with CUPS on Feisty Fawn 7.04 desktop (!) version and what was the laserprinter (no inktjet) and how about the connection (like parallel or usb or...) and how are all programs (pdf, OpenOffice, texteditor, gimp, what more, all of them) printing for you? So who can inform me positively on a laserprinter configured in CUPS succesfully without hassle on Feisty Fawn 7.04 desktop (!) and what about the connection.

Most HP laser jet printers work well in Ubuntu.  Get one with a network card.

---

### Post by oldos2er on 2007-07-30
I have an older HP Laserjet that works fine in Ubuntu. It's connected to my computer via a parallel-to-USB cable. The only caveat I found in installing it was that printers need to be on before Ubuntu will recognize them.

---

### Post by vexorian on 2007-07-30
I had: with a Hp deskjet 3420.


Well not immediate.

I have trashed my color ink years ago since it is too expensive and all what I do doesn't require it, so it is not installed.

So when I tried to print in Linux it didn't print at all, it however took the paper you gave it and pretended to print. I was able to figure out that if the print mode is not set to grayscale, the printer will think it should use color ink and since that wasn't there the printer doesn't do anything.

Somehow, I got more printer issues in windows than Ubuntu, sometimes when I try to print from office sometimes a "System error" message from the printer pops up o_O.

---

### Post by asmoore82 on 2007-07-30
I work at the central office of the local school system ...

they(we) have networked printers and static IPs at the CO but use DHCP in the actual schools...

Ubuntu 7.04 on my laptop:
I just clicked add a new printer and CUPS worked furiously for a few seconds and then
presented me a list of Every available printer in the building AND its Model AND its IP Address.

Perfection.

---

### Post by stchman on 2007-07-31
> **asmoore82 said:**
> I work at the central office of the local school system ...

they(we) have networked printers and static IPs at the CO but use DHCP in the actual schools...

Ubuntu 7.04 on my laptop:
I just clicked add a new printer and CUPS worked furiously for a few seconds and then
presented me a list of Every available printer in the building AND its Model AND its IP Address.

Perfection.

I love CUPS in Feisty.  It is absolutely awesome.  Takes the guess work out of it.

---

