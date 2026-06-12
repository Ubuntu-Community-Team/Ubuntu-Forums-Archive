---
title: "Installing printer"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by wirelessman on 2007-01-01
I have installed Ubuntu a number of times as a free standing units with out a printer. This weekend I installed 6.10 on a friends computer, but was unable to install her printer, HP 610CL. Should I try 5.10 or 6.06? Is one distro better than the other about installing a printer? The printer had worked on 5.10!

---

### Post by OMRebel on 2007-01-01
I looked in Cups, and the driver is there for that printer.  What problem are you actually running into?

---

### Post by wirelessman on 2007-01-01
I can find the printer in the 'printer wizard", but when I test print, the printer doesn't respond.

---

### Post by OMRebel on 2007-01-01
Does Ubuntu detect the printer at all?  If not, then I'd check the cable connections on the printer.  If it's USB, go ahead and power the printer and PC off, and then disconnect the USB cable from both the printer and PC, and reattach the cable, but plug the cable into another port on the PC.  Turn it on, and then see if Ubuntu detects it, and go through and reinstall it and try a print page.

---

### Post by wirelessman on 2007-01-01
Ubuntu doesn't see the printer, its not usb. I've turn the printer on and off, etc. It worked with 5.10.....we added more memory and installed 6.10. We thought the printer would be easy as beforel, not.  Thats why I wonder if moving back to 6.06 or 5.10 would be the answer?

---

### Post by Sef on 2007-01-01
What's your make and model of the printer?  How are you connecting it?

---

### Post by halitech on 2007-01-01
according to here:

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_610CL]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_610CL")

that printer should work like a charm. you sy it's not USB so I'm guessing it's on LPT1 cause I don't think those models have ethernet connections on them.

Check that link out, there should be more info that can help you out.

---

### Post by wirelessman on 2007-01-01
Its a HP printer  Deskjet model HP 610CL, it uses a printer cable, not usb.

---

### Post by Sef on 2007-01-01
When installing under System > Administration > Printing make sure you click on forward, not install.  Did you do that or click install?

---

### Post by wirelessman on 2007-01-01
I click on forward. ........ I've done this before and Ubuntu picked it up, that is on 5.10 not 6.10..... should it matter what distro I use?

---

### Post by Sef on 2007-01-01
It should not matter, but at times it can.   Possibly some piece of code was removed; hence, your problem with it.

---

