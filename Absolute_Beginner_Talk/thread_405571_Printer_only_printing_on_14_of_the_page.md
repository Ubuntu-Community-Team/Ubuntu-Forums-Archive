---
title: "Printer only printing on 1/4 of the page?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by SSB on 2007-04-09
I just got a Canon Pixma MP600 printer. It works fine in windows as one would expect, however in Ubuntu, it only uses a little more than 1/4 of the page instead of printing on all of it. I'm using the suggested driver in Ubuntu which recognizes the printer as a "MultiPASS-C2500" using the "bjc600" driver. Under the "detected printer" dialog it does recognize it as an MP600. I have tried changing PageRegion to "US Letter" as well as a bunch of others, all to no avail. I mean.. it works, just not how I want it to.


Running on Edgy.

---

### Post by crispy_420 on 2007-04-10
dpi set to high?

---

### Post by rvanderblom on 2007-04-17
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/3896](https://answers.launchpad.net/ubuntu/+question/3896) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[https://answers.launchpad.net/ubuntu/+question/3896](https://answers.launchpad.net/ubuntu/+question/3896)

If you follow the link there are some solutions provided to you're question. My mother in law has the same, I'll let you know whether it works.

---

### Post by TURNER on 2007-04-17
Perhaps try:

Menu:

System -> Administration -> printing

Right click your printer and select  properties, followed by the paper tab, check that its set to A4 or whatever size you are trying to achieve.

Just an idea....

EDIT: sorry just read again and realised that you tried this already, usually when I have problems I skip the obvious stuff in favour of a more technical explanation....only to find later that a simple resolution actually exists

---

### Post by Seisen on 2007-04-17
This might help you and you can always download the .rpm file and use alien to make them in .deb files.

[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_.26_use_.rpm_to_.deb_Converter_.28Alien.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_.26_use_.rpm_to_.deb_Converter_.28Alien.29")

---

### Post by ramjet_1953 on 2007-04-18
Check out this link:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600)

It looks like TurboPrint may be the go:

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

Regards,
Roger 8-)

---

### Post by SSB on 2007-04-30
This turbprint works great except for the fact that this free version plants a huge "TURBOPRINT FOR LINUX!" logo right in the middle of anything I print. I'm not about to dish out 40 bucks for a printer driver for Linux.

---

