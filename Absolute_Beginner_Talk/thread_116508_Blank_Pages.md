---
title: "Blank Pages"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by madddonkey255 on 2006-01-12
When I try to print something it sounds like it is printing but only blank pages come out.

---

### Post by madddonkey255 on 2006-01-12
Sorry I forgot to add that I have an HP 3650 printer.

---

### Post by bscbrit on 2006-01-14
Did you successfully print a test page during the CUPS installation of your printer, or are you still at the install stage and not having much success?

---

### Post by Madpilot on 2006-01-14
Your printer is listed here, with some hints for getting it working: [https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters) -- the comment is "Not detected. Have to choose it from the list in Gnome printer install." but it's listed as working after that.

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3650](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3650) lists it as working "Mostly" and has a few more details & hints.

---

### Post by madddonkey255 on 2006-01-17
It won't print a test page.  I think I've got it installed it says ready underneath it  in the printers menu.  The job gets sent to the printer and it prints but nothing gets printed on the paper, I've replaced the ink cartridge and that didn't help.

---

### Post by bscbrit on 2006-01-18
Check first of all that you are not printing to a file, rather than to the device.  At the top of the print dialogue the option is given for selecting file or device. i.e do not print by pressing Ctrl-P but select File -> Print and look at what the dialogue indicates.
Check also that you are printing to the correct device i.e. that your printer is selected as the default printer.

---

### Post by madddonkey255 on 2006-01-19
I finally got it working but it doesn't really seem right.  Turns out the problem was that I had no color cartridge in the printer, HP suggests you do that if your color cartridge is low so that it only prints black.  I only print notes and papers for class so color was never necessary.  Right before I switched to ubuntu my notes and such started to become oddly colored instead of black; I just assumed my black had run out and the colors were running low also.  I replaced the black and took the color out so it would be forced to print from the black cartridge.  Now that my printer is working I was wondering if it's just using the color cartridge all the time, since it only works to print black when the color cartridge is in.

---

### Post by bscbrit on 2006-01-19
I'm only guessing, but perhaps the linux driver is not quite as smart as the manufacture's version.  Not surprising if it has been reverse engineered...  maybe the driver writer only ever used it with full cartridges and therefore never knew that the problem existed?  

The only thing that I can suggest is that, if you ever solve the problem or find out why it occurs, you come back here to post your findings so that others can benefit from it.  :D

---

### Post by ReaderRat on 2006-11-27
[quote=bscbrit]The only thing that I can suggest is that, if you ever solve the problem or find out why it occurs, you come back here to post your findings so that others can benefit from it.[/quote]
Someone did find this useful....thanks bscbrit and maddonkey255...

---

