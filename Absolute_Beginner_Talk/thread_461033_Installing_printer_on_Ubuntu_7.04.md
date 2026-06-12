---
title: "Installing printer on Ubuntu 7.04"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by andypeter on 2007-06-01
I am new to Ubuntu.  I tried the live CD a few times before, but I finally broke down and installed it on my system.  I have my computer hooked up at my office on my wireless network where I have 2 printers.  One printer is a HP LaserJet 2100 the other is a Canon ImageRunner 3530 digital copier.  I was able to find the LaserJet driver on Ubuntu's add printer list.  When I go to print I get: "%!PS-Adobe-3.0  %%HiResBoundingBox: 0 0 612 792  %%Creator: Mozilla PostScript modul" or a similar error followed by blank pieces of paper.  When I print to the Canon IR 3530 (I manually added the driver from the Canon website) I just get a couple beeps followed by an error on the copier saying "6156 Printer PDL IMG Invalid Data".  

I am assuming that I am doing something wrong.  At least I am getting the right printers to beep or print out gibberish... it is just that I need to print things from time to time.  Would anyone be able to shed light into this problem?  I appreciate it! :)

---

### Post by hummingbird59 on 2007-06-01
I don't know if this will be helpful but I also have an HP LAserjet 6L and a Canon both of which set up fairly easily at first.  However, after just a few days, I had to uninstall both and reinstall because CUPS or something kept switching my local printer to network and my HP would not print, the Canon was garbled....Anyway, long story short, I had to uninstall everything and now I can only use my HP, ie attaching other printers to my pc and installing them using the printer config utilty messes everything up.  I have filed a bug on launchpad  but no response so far.  Anyway, try getting your HP up and running by reinstalling it and only it via printer config utility.  It may be helpful to uninstall, reboot and reinstall.  Wish I knew more!  Good luck!

---

### Post by Seisen on 2007-06-01
Here they recommend the pxlmono driver for you HP.

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_2100]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_2100")

I really couldn't find anything about the Canon copier but somebody else might know.

---

