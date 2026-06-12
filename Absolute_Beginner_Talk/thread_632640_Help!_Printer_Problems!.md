---
title: "Help! Printer Problems!"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-05
How do I get a printer working?  I plugged it in, and told my document to print, but it doesn't do anything when i tell it to.  Is there a way to configure a printer, or to make it recognize it? 
What should I do?

---

### Post by LowSky on 2007-12-05
what kind of printer? what version of ubuntu?

---

### Post by Sef on 2007-12-05
What is your make and model of your printer?

If you have an HP, Epson, or Brother, likely it will work.   If you have a Lexmark, likely it is a paperweight.

---

### Post by jordank on 2007-12-05
It's a Canon MP180
Running Gutsy Gibbon.

---

### Post by tonymoloney on 2007-12-05
People have so many problems getting their printers to work that I feel that there should be a separate section within the forum just for printing problems.

---

### Post by jordank on 2007-12-05
That would be helpful.  But does no one know how to get this printer running?

---

### Post by stchman on 2007-12-05
> **jordank said:**
> It's a Canon MP180
Running Gutsy Gibbon.

According to the linux printing website the Pixma MP170 works mostly.

The MP180 is probably very similar to the MP170 besides speed.

The page says to use the gnutenprint driver.

[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP170](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP170)

Give it a try and let us know.

---

### Post by ArtInvent on 2007-12-05
Basically, if the printer is plugged into USB it will be recognized but you will probably have to set it up. Try going to System | Administration | Printing. If you don't see your printer, try the Add Printer button and go from there. Find your printer or the closest thing to it. Try to It's generally best to use the Gutenprint drivers if they are available. 

If you see your printer already present, go into it's properties to make sure the appropriate driver is selected.

Linux drivers are built into the kernel, you generally don't add them from external sources though in theory that is possible.

In my Feisty setup I don't see the MP180 driver but I see the MP150 with Gutenprint drivers so that might be the closest. Try that.

---

### Post by jordank on 2007-12-05
How do I use gnutenprint drivers, how do I get them?
Also, how do I locate a printer if it doesnt show up?

---

