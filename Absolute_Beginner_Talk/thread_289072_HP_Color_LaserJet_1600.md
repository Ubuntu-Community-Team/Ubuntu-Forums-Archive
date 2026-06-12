---
title: "HP Color LaserJet 1600"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by mengd2002 on 2006-10-30
Does anyone know if there is a driver for the HP Color LaserJet 1600, and how do I install it?  I tried using the driver for the 1500 series printer but it didn't work.  Nothing printed.

Thanks,
Don

---

### Post by raqball on 2006-10-30
Try this site:

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_1600](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_1600)

---

### Post by happy-and-lost on 2006-10-30
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_1600](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-Color_LaserJet_1600)

Looks like you need the foo2hp driver

---

### Post by mlb on 2007-12-28
This driver does not  work for me... after printing three or four pages in row te printer gets locked and needs to be restarted, then entire printing job is sent to printer again, is locked again and so on... it happens when printing from linux, from windows... the hp1600 driver has some bugs :sad: Tested on ubuntu 7.10 with CUPS

---

### Post by Mad_Dawg on 2007-12-28
If you are having the same problem in Windows and Linux, IMHO, the problem is the printer itself, not the driver.

---

### Post by odinb on 2008-01-15
Have you followed the instructions on this page: [http://foo2hp.rkkda.com/](http://foo2hp.rkkda.com/)

---

### Post by MoikleCollins on 2008-03-07
And did any of this work, please?  I'm thinking of getting a HPCLJ1600 to replace the aging 1500 that doesn't work with either Ubuntu or Vista (Yes, I made a bad mistake and bought a laptop with Vista ).  Thanks and smiles, Michael

---

### Post by quill3033 on 2008-03-26
I'm thinking of buying a HP Laser 1600 also - they are giving me the option of trialing for a week and returning it if it doesn't work with Ubuntu.
I just went to the page suggested about (the foo page :-) and it says there:

*** DON'T USE the foo2zjs package from Ubuntu, SUSE, Mandrake/Manrivia, Debian, RedHat, Gentoo, MacOSX, or BSD!
*** Download it here and follow the directions below.

and then below it says the "gnome-cups-manager has a bug in it". I was just congratulating myself on having all the programs listed on that page and the actual procedure he describes seems a bit difficult so I'll try the printer with what I've got and if that doesn't work then I'll try downloading and following the procedure he describes. 

btw I still have Ubuntu 6.06LTS and generally happy with it.

the linuxprinting site seems to mostly have rpm format and i have found them very difficult to unpack etc. (sorry not using the right language - v tired)

I had been trying to revive a really old nec silentwriter superscript 610 from 1994 or something that still works beautifully on a v old computer w Windows98...

the system gave me a couple of options that it thought it was but theydidn't work. 

Anyway, I'll report how I go if I get the printer. If anyone else has it and is using it, I'd love to hear about it.

---

### Post by LowSky on 2008-03-26
HP has mad a good and simple program to help with HP printer issues

[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

---

### Post by kolisikepu on 2008-03-26
I use the 1600 printer and it's working on pc with no problems.

I'm running Vista Ultimate and {drum roll} Ubuntu 7.10.

---

### Post by Sef on 2008-03-26
> HP has mad a good and simple program to help with HP printer issues

[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

The site says that the HP Laser Jet is [unsupported]("http://hplip.sourceforge.net/supported_devices/unsupported.html") in HPLIP.

> This driver does not work for me... after printing three or four pages in row te printer gets locked and needs to be restarted, then entire printing job is sent to printer again, is locked again and so on... it happens when printing from linux, from windows... the hp1600 driver has some bugs  Tested on ubuntu 7.10 with CUPS

Did you check with [foo2hp forums]("http://foo2zjs.rkkda.com/forum/")?

---

### Post by LowSky on 2008-03-26
Wooops... worse comes to worse a new HP printer can be purchased for under $100

---

### Post by quill3033 on 2008-04-03
> **quill3033 said:**
> I'm thinking of buying a HP Laser 1600 also - they are giving me the option of trialing for a week and returning it if it doesn't work with Ubuntu.
I just went to the page suggested about (the foo page :-) and it says there:
Anyway, I'll report how I go if I get the printer. If anyone else has it and is using it, I'd love to hear about it.

Ok I have bought the 1600 and brought it home and it's working. I downloaded the Foo stuff,  untarred it and then went to the PPD for the printer and copied it to the desktop.  The print manager thing recognised it when I clicked on add printer and it asked for 'install driver' and I went to the PDD on the desktop from there and ... it worked!!!

I had to go to the actual printer menu (physically ON THE PRINTER) and went to system setup color calibration and I asked 'calibrate > now' and it worked after that. Before that it was only printing the b&w and any colour pages were just a blur on the page. 

So I am soooooooooo pleased. (btw I have Ubuntu 6.06) 
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

