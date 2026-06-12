---
title: "Conon Printer driver"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by avanrens on 2007-04-24
I have had Ubuntu installed for two weeks and still haven't being able to install a printer driver for my Canon ip4000. I have followed all the directions on the installation process. If I now try to install  anew printer from System>Administration>Printing>New Printer. the system recognizes the printer is connected I then go on to install the driver. I locate the Canon_ip4000.pdd file, but when I go to install the file I get a dialog box which tells me the driver is already installed, but there is no printer icon in the New printer dialog box. I have installed TurboPrint and this runs perfectly, but won't double side print or print on cd's and costs almost the price of a new printer

---

### Post by phidia on 2007-04-24
[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP4000](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP4000)

IMO the above site, linuxprinting.org, is the best info source when you're having printer probs.
Make sure you have the latest driver installed per the how-to in the link.

---

### Post by avanrens on 2007-04-24
I have downloaded gutenprint to my Desktop and when I use Alien to convert the rpm file I get this message Must run as root to convert to deb format (or you may use fakeroot).

---

### Post by bobplano on 2007-04-24
just run it in the terminal. i'm not sure of the exact command because i don't have alien but i assume it would be something like

sudo alien *package name*

---

### Post by avanrens on 2007-04-24
Yes I am running it in terminal and this is the error I get. "Must run as root to convert to deb format (or you may use fakeroot)".

---

### Post by ubunter1 on 2007-04-24
do we need to extract the rpm file first? then sudo alien etc?.

---

### Post by ramjet_1953 on 2007-04-24
Much easier for you if you go into the Synaptic package manager and do a search under [COLOR="Blue"]foomatic-db-gutenprint[/COLOR]

This is already in deb format and has been set-up for Ubuntu.

Regards,
Roger :cool:

---

### Post by ubunter1 on 2007-04-24
thanks ill try that,hopefully it will work with this printer.rob.

---

### Post by avanrens on 2007-04-27
Installed TurboPrint, has all my printer functions but it cost money but worth it in the long run.

---

