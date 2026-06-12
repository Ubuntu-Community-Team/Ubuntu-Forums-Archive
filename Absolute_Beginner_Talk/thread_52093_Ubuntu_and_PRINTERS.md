---
title: "Ubuntu and PRINTERS"
date: 2005-07-26
forum: Absolute Beginner Talk
---

### Post by xbilly on 2005-07-26
I cannot get my printer to work. Ubuntu claims that it is printing and complete, but nothing really happens. My properties look as such:

Under the general tab, The description  and name is "imagerunner-330s"
and under Driver:
the Manufacturer is CANON
the model is imageRunner 330s
and the Driver is hpijs (recommended) (Suggested)

I kept the driver only because it was siggested and recommended. I am guessing this could be the problem though, that and the fact my Printer is a CANON i250 and not an imageRunner. I do not have the disk anymore with the drivers, unfortunately, and when i install the driver off Caonon's web site, i can only get windows and mac versions and even with WINE installed, I can't get the driver. PLEASE HELP!

---

### Post by az on 2005-07-26
Looking at things on google, it looks like the i250 is a bubble-jet printer.  Try using the canon bjc250 printer driver (gimpprint)

If that works, *please* file a bug report so that this gets fixed.  Post back if this is the case and you have trouble reposting this bug.

bugzilla.ubuntu.com

here are some links of interest:


linuxprinting.org

[http://linuxprinting.org/printer_list.cgi?make=Canon](http://linuxprinting.org/printer_list.cgi?make=Canon)

[http://linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-250](http://linuxprinting.org/show_printer.cgi?recnum=Canon-BJC-250)

---

### Post by xbilly on 2005-07-26
Well I just wanted to say that I read around and found that TurbuPrint, a commercial program, fixed my problem. the site is [http://www.turboprint.de/](http://www.turboprint.de/)

I installed it (they gave really good instructions on installing it that even i was able to follow)

After installing it and running it, I just had to set up a couple of things (like the name of my printer and a name to associate it with when I select my printer from a menu) and I had it print out a test page and it just finished printing now.

So If anyone else has some printer problems, I suggest checking out turboPrint. They have a free version and it worked. The site is available in english and some othe rlanguage.

[http://www.turboprint.de/](http://www.turboprint.de/)

---

### Post by bardoz on 2005-08-01
[QUOTE=xbilly]So If anyone else has some printer problems, I suggest checking out turboPrint. They have a free version and it worked. The site is available in english and some othe rlanguage.

[http://www.turboprint.de/](http://www.turboprint.de/)[/QUOTE]
I just have to say thank you! Turboprint turned out to be just the right solution for me. Their printer drivers support a large amount of printers from Canon, Epson and Brother.

I have a Canon PIXMA MP760 myself. Didn't find this one on the printer list, but I found the MP750. Tried that driver and it works like a charm!

Cheers!

 \\:D/

---

### Post by rherman on 2005-08-03
I don't wish to install another printer handler just yet. Brother had the appropriate files. They are rawtobr filterMFC4800 and psconvert. I do not know where to put these or specify their use. Currently they are in /usr/local/Brother/lpd

Thanks.

Rob

---

