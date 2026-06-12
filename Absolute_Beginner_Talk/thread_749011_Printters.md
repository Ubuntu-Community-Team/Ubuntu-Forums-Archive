---
title: "Printters"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by alpdo on 2008-04-08
hey guys i have 2 epson printers  fx 2175 and lx-300+...
how do i install it... drivers???

---

### Post by paydaydaddy on 2008-04-08
Try this info page for starters.
[https://help.ubuntu.com/7.10/printing/C/index.html](https://help.ubuntu.com/7.10/printing/C/index.html)

---

### Post by ramjet_1953 on 2008-04-08
Here's some information on the lx-300: 

[http://openprinting.org/show_printer.cgi?recnum=Epson-LX-300](http://openprinting.org/show_printer.cgi?recnum=Epson-LX-300)

I couldn't find a listing for the fx-2175 in the linux printing database. However as I believe that both of these printers are dot matrix, they almost certainly will use the ESC/P protocol, so almost any generic Epson driver will probably work.

Regards,
Roger :cool:

---

### Post by alpdo on 2008-04-09
can any one pls tell me how can i install my epson fx 2175 on my ubuntu box

---

### Post by virilc on 2008-05-31
**DISCOVERY!** For Epson FX-2175, we were having font issues with the Generic ESC/P driver. We installed the Generic --> Dot Matrix --> IBM driver ... better output. By the way, it was tried on Kubuntu 7.10. For your information. :)

---

### Post by alpdo on 2008-06-02
ok tanks ill try on my box

---

### Post by feest on 2008-06-02
system > administration > printing (or what is it called?) 
new printer > follow wizard

---

