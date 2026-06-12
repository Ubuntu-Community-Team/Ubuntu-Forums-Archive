---
title: "lpinfo -v does not recognize printer"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by mhills on 2007-06-29
I have installed ubuntu 7.04 and everything works well except printing. The command
lpinfo -v does not pick up a printer which is connected to a usb socket and switched on.
Attempts to add a printer via system>adminstration>printer also failed.

The printer is HP-LaserJet_5L

Any suggestions about what to do next are welcome,

Michael

---

### Post by Seisen on 2007-06-29
Are you sure its usb cables and not IEEE cables?

---

### Post by mhills on 2007-06-29
How do I tell the difference between usb and IEEE cables. The cable connecting the printer fits  into the usb socket.

Michael

---

### Post by Seisen on 2007-06-29
Maybe it has a usb port on the printer than, HP's webstie only mentions something about IEEE cables. Can you access cups from your browser

[http://localhost:631]("http://localhost:631")

---

### Post by mhills on 2007-06-29
What do you have in mind?

---

### Post by Seisen on 2007-06-29
If you can access cups through your browser you might be able to set up your printer.

---

### Post by mhills on 2007-06-29
OK, but I am not sure what access cups through my browser actually means.

---

### Post by Seisen on 2007-06-29
Type this in the browser

[http://localhost:631]("http://localhost:631") it will either say page not found or it will bring up cups.

---

### Post by mhills on 2007-06-30
Thanks for your help. I blush to admit that switching off everything at the mains and starting again fixed the problem, but at least I learned a couple of useful things on the way, namely lsusb to list all devices connected to a usb port and lpinfo -v to list all printers.

---

### Post by Seisen on 2007-06-30
At least its working again and you learned some new things along the way that is all the matters.

---

