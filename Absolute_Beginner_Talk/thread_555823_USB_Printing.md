---
title: "USB Printing"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by getaboat on 2007-09-20
Having got fed up with flaky network printing to my Brother laser on a W98 box that is not used often I put the laser on a USB port on my Dapper box. It all added Ok as a local printer and I printed out my daughters homework. A few hours later and it wasn't working. I noticed that it now thought it was network printer on usb://Brother etc.

I've dug out an ancient parallel port cable deleted and added the printer again and now seems all OK - though it didn't detect the printer.

Anyone with any ideas what is going on? Does Dapper lose interest in USB ports if no activity?

I have a crappy old Deskjet on parallel on my Fiesty box and that is always OK - USB devices there are a bit flaky though at times.

Thanks

---

### Post by Daveth on 2007-09-20
can you give us some detail on the makes of the printers? I have known Ubuntu lose interest in usb mice but not printers. Did the homework print job get executed properly? and was the feww hours after a re-boot, or just sat there running?

---

### Post by getaboat on 2007-09-20
Brother HL-1430. When it worked as a network printer on W98 it worked fine. It was about three hours from putting it on the USB and setting up as a new local printer and it working fine - computer left on so no re-boots and then about two hours later my son tried to print his home work and the prints said printing (but it wasn't). Restarting CUPs made no difference so delete printer, move from USB to parallel, Add printer (#LPT1) and it works again.

When it was added on USB it was spotted as an existing printer. Not spotted when added on parallel

If I ever get a quiet moment - I'll repeat the exercise.

Thanks

---

### Post by Daveth on 2007-09-20
odd, rated as a 3 tux priner here

[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1430](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1430)

there are a couple of driver options there to explore as well.

---

