---
title: "Can't get HP laserjet printer to work"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Jensor on 2007-02-08
I am trying to get my printer to work in ubuntu 6.06.1 LTS with kernal 2.6.15-magma.


After going through System-Administration-Printers and adding HP Laserjet  4P, it looked for HP-Laserjet_4P-hpijs.ppd and apparently installed it. 

To check to see if it worked, I went to System-Help and from the file menu selected print this page.  Then a window came up with 3 offerings - Create a PDF document, Generic Postscript, and Laserjet-4P.  I selected my printer (Laserjet-4P) and clicked on print.  It looked like it accepted this, however the printer stayed dormant.

I then selected System-Administration-Printing and a window comes up and I right clicked on my HP Laserjet 4P and selected jobs from the drop down list and then got another window which indicates that job 1 is printing.  Printer is still dormant.

Any ideas on how to fix this?

I need to mention that my Linux machine is not on the internet.  The only way  I can access and down load any files is through another PC on Windows XP and transfer the files to the Linux machine via a flash memory stick.  I have already learned the hardway that Ubuntu assumes you have an internet connection.  Then bombs out if you don't.  I'm in the process of getting an external modem to get past that problem.

Jack Ensor

---

### Post by Madpilot on 2007-02-09
[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4P](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4P)

The link above is Linuxprinting's database entry for your printer; it should work perfectly, according to the synopsis.

Have a look thru the advice on that page; Linux printing is not as straightforward as it should be but the linuxprinting pages are always useful.

Good luck, and be glad it's a HP, not a Lexmark or something - HP generally works well on Linux...

---

### Post by peakoiler on 2008-01-11
Thanks for the link. You are correct it did work perfectly,   I recently installed Gutsy on my office computer (no more windows!) and had trouble getting the printer to work.  Now my old reliable laserjet 4p is up and running.

---

### Post by stchman on 2008-01-11
> **Jensor said:**
> I am trying to get my printer to work in ubuntu 6.06.1 LTS with kernal 2.6.15-magma.


After going through System-Administration-Printers and adding HP Laserjet  4P, it looked for HP-Laserjet_4P-hpijs.ppd and apparently installed it. 

To check to see if it worked, I went to System-Help and from the file menu selected print this page.  Then a window came up with 3 offerings - Create a PDF document, Generic Postscript, and Laserjet-4P.  I selected my printer (Laserjet-4P) and clicked on print.  It looked like it accepted this, however the printer stayed dormant.

I then selected System-Administration-Printing and a window comes up and I right clicked on my HP Laserjet 4P and selected jobs from the drop down list and then got another window which indicates that job 1 is printing.  Printer is still dormant.

Any ideas on how to fix this?

I need to mention that my Linux machine is not on the internet.  The only way  I can access and down load any files is through another PC on Windows XP and transfer the files to the Linux machine via a flash memory stick.  I have already learned the hardway that Ubuntu assumes you have an internet connection.  Then bombs out if you don't.  I'm in the process of getting an external modem to get past that problem.

Jack Ensor

That printer is reported to work perfectly under Linux using the hpijs driver.  That printer should work out of the box.  You will probably have to change the paper from A4 to US Letter.

[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4P](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4P)

---

