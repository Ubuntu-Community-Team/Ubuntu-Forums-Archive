---
title: "Printer's failure"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-06-21
I've got a laser printer (EpsonEPL 6200L); it keeps the jobs on pause and I've got this message on the tab which describes its properties:
/usr/lib/cups/filter/foomatic-rip failed

I've tried to reinstall it but it was worthless

Any hint? Thanks.:)

---

### Post by bscbrit on 2006-06-21
Is it connected using USB or the parallel interface?

Has the printer worked before with linux (i.e. has this fault just appeared?) or have you never had it working under linux?

---

### Post by %hMa@?b&lt;C on 2006-06-21
try this

[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-6200L](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-6200L)

---

### Post by helphope on 2006-06-21
Thanks for replying :D 

> Is it connected using USB or the parallel interface?

Has the printer worked before with linux (i.e. has this fault just appeared?) or have you never had it working under linux?
It's connected via USB and it has never worked under Linux.

> try this

[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-6200L](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-6200L)

I saw your link. Here are the instructions:
1) Install gs-afpl (not GPL :( ) , configure the printer via System-->Administration-->Printers.
2) Modify the file sited at /etc/cups/ppd/EPL-6200L.ppd . Change the "gs" command and put "gs-afpl" instead.  #-o 
3) Download "Epson EPL-5x00L/EPL-6x00L Printer Driver" from Sourceforge at:
[http://sourceforge.net/projects/epsonepl/](http://sourceforge.net/projects/epsonepl/)

I went thourough steps 1 and 3 ( I downloaded the file on the desktop; wel I hope the right one 'cause there are 3 files).
But I don't know how to go on with the second step.#-o 
Thanks again

---

### Post by bscbrit on 2006-06-22
sudo gedit /etc/cups/ppd/EPL-6200L.ppd

will open the file in an editor using root privileges.  Make your changes and then save the file.

---

### Post by helphope on 2006-06-22
[QUOTE=bscbrit]sudo gedit /etc/cups/ppd/EPL-6200L.ppd

will open the file in an editor using root privileges.  Make your changes and then save the file.[/QUOTE]
Thanks. I'll try right now.;)

---

