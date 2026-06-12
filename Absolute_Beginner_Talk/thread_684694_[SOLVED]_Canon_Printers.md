---
title: "[SOLVED] Canon Printers"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by tad1073 on 2008-02-01
does anyone know where i can find drivers for a canon pixma mp780

---

### Post by Philiptheorganist on 2008-02-01
'd also like to know where to get drivers for a canon MP500.  i am running ubuntu 7.04 Feisty.I will need to share the printer with a PC running XP Home Edition. Thanks

---

### Post by kellemes on 2008-02-01
See the following link.
[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP780](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP780)

As you can see you need the commercial Turboprint driver, see..
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

Canon + GNU/Linux = bad.

---

### Post by kellemes on 2008-02-01
> **Philiptheorganist said:**
> 'd also like to know where to get drivers for a canon MP500.  i am running ubuntu 7.04 Feisty.I will need to share the printer with a PC running XP Home Edition. Thanks


Does this work?
[http://ubuntuforums.org/showthread.php?t=282096&page=4&highlight=MP510](http://ubuntuforums.org/showthread.php?t=282096&page=4&highlight=MP510)

---

### Post by iansane on 2008-02-01
if all else fails, My cannon mp150 uses a gutenprint driver listed in the ubuntu built in drivers when adding a printer. Printer and scanner work great.

---

### Post by tad1073 on 2008-02-07
bump...I found some drivers, but I still can't print to the printer. It is a network printer connected to an xp machine.

---

### Post by Benbow on 2008-02-07
I have been trying Hardy Heron (8.4) which isn't on general release until April and I found, to my surprise, that it printed straight away with my Canon Mp170. I have so far used turboprint with Ubuntu and all other linux flavours.
You either buy Turboprint, try Gutenprint (above) or wait until April unless someone can point us in the direction of Hardy Heron's success!!

---

### Post by tad1073 on 2008-02-07
I downloaded gutenprint-5.0.1-1lsb3.1.i486.rpm and turboprint-1.96-4.tgz and neither work for me. I haven't made any changes to the cupsys configuration file so maybe that is the problem, also I read in a thread here about setting your scan address before you scan for network printer. Do you think you could point me in the right direction?

---

### Post by tad1073 on 2008-02-08
Could someone give me some pointers on how to configure my cupsys and samba configuration files. I have read through the documentation (man) pages for both but can't make heads or tails out of them.

---

### Post by tad1073 on 2008-02-08
anybody???!!!

---

### Post by tad1073 on 2008-02-09
bump...

---

### Post by mrsteveman1 on 2008-02-11
Can you get to the cups web interface?

Should be at [http://localhost:631/admin]("http://localhost:631/admin")

---

### Post by tad1073 on 2008-02-12
Yep, I can access that page. I get this error "Unable to connect to CIFS host" but the xp machine is off so I know it is not goin to work. And i also get this error "/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0 failed". I chaned the cupsys file to point to that direcory just grasping for straws.

---

