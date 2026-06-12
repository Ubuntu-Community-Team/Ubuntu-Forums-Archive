---
title: "Illegible (light) Printing in 7.04"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Rumor on 2007-05-16
I've realized a problem with my printer in 7.04. I have an HP DeskJet 895C which is connected to my computer (Running Ubuntu 7.04) and is also shared on our network with two other computers running Windows XP.

This set up worked fine when I was running 6.10 (also 6.04 & 5.10).

When I print from my computer, the printing is so light as to be illegible. It is as though I am out of ink. 

I've noticed that graphics will print, though very faintly, but text does not print at all.

When I print from one of the Windows computers, the printing is just fine. 

I am using the hpijs driver. I've tried the other five drivers but the quality does not noticeably improve. 

What has changed from 6.10 to 7.04 that has rendered printing so poor? What might I do to correct this situation?

---

### Post by markitect on 2007-05-17
you might try going to linuxprinting.org and downloading the ppd file from there [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_895C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_895C)

replace the existing one and see if that helps.

---

### Post by Rumor on 2007-05-17
Thanks for the link. I'll give it a try and let you know how it works out.

---

### Post by Rumor on 2007-05-17
Nope, that wasn't it.

---

### Post by bean77 on 2007-05-19
> **markitect said:**
> you might try going to linuxprinting.org and downloading the ppd file from there [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_895C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_895C)

replace the existing one and see if that helps.

How do I replace the old one?  I am having the same problem.  I have a Canon i560 (USB)

---

### Post by Rumor on 2007-05-19
I downloaded the driver file and then browsed to where I put it from within the printer setup when it came to the driver screen.

Yours would be here: [http://openprinting.org/show_printer.cgi?recnum=Canon-i560](http://openprinting.org/show_printer.cgi?recnum=Canon-i560)

---

