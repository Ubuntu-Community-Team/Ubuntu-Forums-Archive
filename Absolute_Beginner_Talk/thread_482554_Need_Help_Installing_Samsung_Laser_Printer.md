---
title: "Need Help Installing Samsung Laser Printer"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by john wagner on 2007-06-23
[SIZE="2"]Here I am again!  I need help installing drivers for the Samsung Colour Laser Printer CLP-300N.  I am running Dapper Drake 6.06 and cannot fathom how to get my laser printer to work with it.

I have tried to install the Linux drivers included on the CD that came with the printer (Linux distributions : Redhat 6.x, Mandrake 7.x, SuSE 6.x, Debian 2.2, Caldera OpenLinux 3.x, TurboLinux, Slackware 7.x, Linux/PPC, Yellow Dog, and newer versions.  No Ubuntu listed, just the generic Debian 2.2) all without any luck.  I went to the Samsung website, and this is what they say to do[/SIZE]:[COLOR="Red"]


[Unified Linux Driver Install Guide]

1. Make sure that you connect your machine to your computer.
Turn both the computer and the machine on.
2. When the Administrator Login window appears, type in root in the Login field
and enter the system password.
3. Download and extract the driver
[root@localhost root]#tar xzf [Downloaded File Name(XXXX.tar.gz)]
4. The driver will be extracted as ''cdroot'' folder in current path.
5. Execute installation program.
[root@localhost root]#./cdroot/autorun
6. When the welcome screen appears, click ''Next'' and proceed installation.

[Ubuntu OS Installation)

1. Download and extract the driver
2. Open ''Root Terminal''
3. Execute installation program.
$ sudo cdroot/autorun
4. After intall, PPD path is set again.
$ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung
5. Execute Configurator, and Add your printer model name by Add Printer[/COLOR]

[SIZE="2"]Okay, tried it, no luck.  The "AddPrinter" sees the printer, but it wont do anything with it.  When I try to print something, the CLP-300N isnt listed.
It is listed in the configuration tool[/SIZE].

In case it matters, Samsung lists these as required:[SIZE="1"]
[COLOR="Red"]Requirements :
- GTK+ 1.2 libraries ; these usually come with the GNOME desktop environment,
  but if your distribution didn't install those by default, you will need to
  install them before you can use the graphical tools from this package.
- A working Ghostscript installation
- CUPS 1.1.x is the preferred printing system for this package, but the
  Linux Package will accommodate any other printing system based on LPD.
  CUPS 1.1.14 packages are provided as a convenience with this program, and can
  be installed or upgraded from the installer. However, users of Debian and
  Slackware distributions should make sure they have an active printing system
  (such as LPD) before proceeding with the installation.[/COLOR][/SIZE]


[SIZE="2"]HELP!!!!!!  I am a newbie in need of knowledge (use small words please!)[/SIZE]

john

---

### Post by john wagner on 2007-06-23
So, from the resounding silence, I gather that I'm screwed....

Sigh...  Too bad, nice printer.  Works well in Windoze (wife's laptop), my own is Dapper only.  Guess I better consider switcjing back to Windblows only (for production/income).  I cannot afford to NOT have a quality laser at my fingertips.

john

---

### Post by john wagner on 2007-06-24
[SIZE="2"]Just trying to reaquire an audience for this thread!  HELP ME!!!!!!!!!!!  PULEEEEEEEEASE!!!!!!!!

John[/SIZE]

---

### Post by mikeyandmary on 2007-07-12
Hi John,

There's some bad news and some good news... Please remember though that this is just my experience and many others may have had greater success / better skills

For the record, I have 1 PC and 2 laptops running ubuntu feisty (previously ran dapper). I bought the Samsung CLP-500 when I was a windows slave and was very frustrated trying to get the printer to work properly. 

Bad news... The linux driver provided by Samsung are rubbish. They only install sporadically and do not allow you to use many of the printer's features. most importantly (from a cost perspective) IT ONLY PRINTS COLOUR!!! 

Good news... The following website is pure GOLD... [http://www.linux-foundation.org/en/OpenPrinting]("http://www.linux-foundation.org/en/OpenPrinting")  (used to be called [www.linuxprinting.org](www.linuxprinting.org) ) This website provides everything you need to know about printers and linux. It tells you which printers work and which don't. It also provides good information on how to install the printer if it works in linux. 

For the CLP-300N go to [http://openprinting.org/show_printer.cgi?recnum=Samsung-CLP-300N]("http://openprinting.org/show_printer.cgi?recnum=Samsung-CLP-300N")
This says that the samsung driver should work fine, but it also provides another driver to try a little further down the page. This page has the info... [http://foo2qpdl.rkkda.com/]("http://foo2qpdl.rkkda.com/") Now I don't have this particular printer but the posts in [www.linuxprinting.org](www.linuxprinting.org) for this printer suggest that it should work. 

I share your pain with the Samsung printers and hope you get your's working soon...
Michael

P.S. If you've already tried my ideas and they didn't work, oh well... Life goes on :confused:

---

### Post by rorre on 2007-08-17
Hi!

Samsung drivers not to work to Ubuntu, you find to help:

[http://foo2qpdl.rkkda.com/](http://foo2qpdl.rkkda.com/)

Configure its ready about 3 minute and work ok.


Quikhelp:

1. $ wget -O foo2zjs.tar.gz
(tai [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz))
2. $ tar zxf foo2zjs.tar.gz
3. $ cd foo2zjs
4. $ make
5. $ sudo make install
6. $ sudo make cups
7. $ sudo gnome-cups-manager

..and when you add printer, make to sure its driver is foo2qpdl.

This works me very well and quikly.

--rorre

---

