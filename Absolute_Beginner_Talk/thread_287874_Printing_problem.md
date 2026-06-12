---
title: "Printing problem"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Hillerd on 2006-10-29
Hi,
I have an Epson Stylus DX4850 printer connected to my USB port. According to the hardware support page [https://wiki.ubuntu.com/HardwareSupportComponentsPrinters]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters")
it should work providing I have "gutenprint 5.0.0". Checking I found "gutenprint 5.0.0 rc2" (running Ubuntu 6.06) on my system.
The problem is that the colors yellow, red, blue are each offset in vertical by 1 cm each. Printing in Windows XP works fine.
Can anyone provide some help to an **absolute** beginner?

Here what I found out:
Epson printer is connected to "local". My old HP printer is connected to CUPS. I do not know what address to enter in the line to make Epson print on CUPS as well.

Do I really need CUPS, I read it is for network printing. My printers are local and I do not want to provide access to them to anyone else.

Sorry, I am completely lost on this, please help?

---

### Post by mahy on 2006-10-29
> **Hillerd said:**
> :
Epson printer is connected to "local". My old HP printer is connected to CUPS. I do not know what address to enter in the line to make Epson print on CUPS as well.

Do I really need CUPS, I read it is for network printing. My printers are local and I do not want to provide access to them to anyone else.


CUPS is not only for network printing. start gnome-cups-manager and follow the wizard. Let us know if it doesn't work. Other than that, i dunno what can be wrong...

---

### Post by Hillerd on 2006-10-29
> start gnome-cups-manager and follow the wizard. 
I used System > Admin > Printer, which I believe is the gnome-cups-manager. It recognizes the printer at lets me install it. 
Proposed printer type of the wizard is "local", could I use that as well?  This is the configuration that messed up the colors.
If I change to network printer CUPS, I need to type an "Address". My HP printer had "usb://HENTER/HP Deskjet 670C", but I do not know, what to enter for the Epson device. (no idea where this HENTER is coming from either).
Maybe I once changed the type to local manually in the past, but I already rebooted the PC and still, it does not propose an address for CUPS.

Thinking, that the misalignment of the colors could be an issue with the driver, I found 
- Gutenprint-5.0.0.tar.bz2 (remember, I have RC2 of that, not the final; but my Archive-Manager does not allow to open it - " Compressed file ends unexpectedly;" - already downloaded twice).
- on Avasys.com Epson drivers of type rpm (Red Hat, I understand)

Could using one of these help?
How can I make the Archive-Manager read the tar.bz2 file, or could the archive really be corrupted?
Can I use an rpm file (System Docu says "better not")

Thanks.

PS: Sorry for the many questions, just started to use Linux 1 week ago.

---

### Post by Hillerd on 2006-10-30
Now I spent another evening on the printer, still no success, the colors are printed by a 1cm offset each.:confused: 
I want to install the last Gutenprint  5.0.0 drivers. Can someone give me instructions how to do so?

---

### Post by Sef on 2006-10-30
Have you checked out [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX4800")?

---

### Post by Hillerd on 2006-11-01
Okay now I have downloaded Gutenberg.5.0.0. The fault was that rc2 (which was provided with the CD) does cause this error for my Epson printer.
Now I follow the instructions to install the ppd, but the installer does not want to do so.
:-k configure says: 
checking for cups-config... no
checking whether to whether to build CUPS driver... no
checking whether to build CUPS PPD files... no
checking whether to build translated CUPS PPD files... no
checking whether to build simplified CUPS PPD files... no
checking whether to place CUPS PPD files at top level... no
checking whether to generate PostScript level 3 PPD files... no

which tells me, it does not want to install the ppd files I need.

Can someone help, please?

---

### Post by Hillerd on 2006-11-01
It's dark again, and the printer is running:) 
okay, for anyone having the same problem:
starting situation: 
[INDENT]Ubuntu 6.06, Printer Epson Stylus DX-4850, color printing is bad
reading through the release notes of Gutenprint: 5.0.0rc2 has this known problem with this printer, it is resolved in the final release 5.0.0[/INDENT]

Solutions a) use Epson-Avasys simple driver
[INDENT]1.download pips-scx4700-cups-2.6.3-1.i386.rpm [[http://www.avasys.jp/english/linux_e/dl_spc.html]](http://www.avasys.jp/english/linux_e/dl_spc.html])
2.install alien from Ubuntu
3.convert rpm to deb
alien pips-scx4700-cups-2.6.3-1.i386.rpm
4.rightclick on  pips-scx4700-cups-2.6.3-1.i386.deb to install
[/INDENT]

Solution b) using Gutenprint driver
[INDENT]1.download gutenprint-5.0.0.tar.bz2 [[http://gutenprint.sourceforge.net/]](http://gutenprint.sourceforge.net/])
2.rightclick to extract
the file readme contains the complete instructions
3.download from Ubuntu
libcupsys2-dev (for cups-config)
libcupsimage-dev (for lcupsimage)
build-essentials to be able to compile the source-code [[https://help.ubuntu.com/ubuntu/desktopguide/C/programming.html#build-essential]](https://help.ubuntu.com/ubuntu/desktopguide/C/programming.html#build-essential])
4.cd gutenprint-5.0.0
./configure
make	
sudo make install	
sudo cups-genppdupdate.5.0	
sudo /etc/init.d/cupsys restart[/INDENT]

So let's try to get the scanner running as well (and fix the problem why after all these trials the WLAN does not work anymore:-k )

---

