---
title: "How do I get the Lexmarz52 printer application?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by rustyDusty on 2008-02-07
Using Lexmark z52 printer.
Ubuntu easily recognised and allowed me to use the printer if I'm just printing a straight plain word document.
But I need the software interface or control application that in WinXP allowed me to choose things like booklet format, dual side printing, poster setting etc.

Lexmark has Linux packages. I downloaded and untarred (is that the right term?) the cjlz52le.tgz. Installed Lexmark package on PC with Kpackage and got this message.

 > 
rpm -U --replacepkgs  '///home/Myname/lexmarkz52-1.0-4.i386.rpm';echo RESULT=$?
error: Failed dependencies:
	/bin/sh is needed by lexmarkz52-1.0-4.i386
	ld-linux.so.2 is needed by lexmarkz52-1.0-4.i386
	libc.so.6 is needed by lexmarkz52-1.0-4.i386
	libdl.so.2 is needed by lexmarkz52-1.0-4.i386
	libgdk-1.2.so.0 is needed by lexmarkz52-1.0-4.i386
	libglib-1.2.so.0 is needed by lexmarkz52-1.0-4.i386
	libgmodule-1.2.so.0 is needed by lexmarkz52-1.0-4.i386
	libgtk-1.2.so.0 is needed by lexmarkz52-1.0-4.i386
	libm.so.6 is needed by lexmarkz52-1.0-4.i386
	libslang.so.1 is needed by lexmarkz52-1.0-4.i386
	libstdc++-libc6.1-1.so.2 is needed by lexmarkz52-1.0-4.i386
	libX11.so.6 is needed by lexmarkz52-1.0-4.i386
	libXext.so.6 is needed by lexmarkz52-1.0-4.i386
	libXi.so.6 is needed by lexmarkz52-1.0-4.i386
	libc.so.6(GLIBC_2.0) is needed by lexmarkz52-1.0-4.i386
	libc.so.6(GLIBC_2.1) is needed by lexmarkz52-1.0-4.i386
RESULT=1

On the right side of the kpackage is a summary listing dependencies:
> summary
Lexmark Z52 Printer driver
version
1.0-4
group
Applications
size
5528619
description
This package contains a printer driver for the Lexmark Z52 printer. It also contains a Graphical User Interface (GUI) utility named lexmarkz52 and is located under /usr/local/lexmark/z52/ directory. This utility can be used to determine the paper size, paper type and print resolution for your print job. It can also be used to perform cartridges operation on the printer. Requires: enscript >= 1.6.1 Requires: ghostscript >= 5.50
url
none
architecture
i386
unsatisfied dependencies
/bin/sh, ld-linux.so.2, libc.so.6, libdl.so.2, libgdk-1.2.so.0, libglib-1.2.so.0, libgmodule-1.2.so.0, libgtk-1.2.so.0, libm.so.6, libslang.so.1, libstdc++-libc6.1-1.so.2, libvdkcompo.so.1, libvdk.so.1, libX11.so.6, libXext.so.6, libXi.so.6, /bin/sh, libc.so.6(GLIBC_2.0), libc.so.6(GLIBC_2.1)
depends
/bin/sh , ld-linux.so.2 , libc.so.6 , libdl.so.2 , libgdk-1.2.so.0 , libglib-1.2.so.0 , libgmodule-1.2.so.0 , libgtk-1.2.so.0 , libm.so.6 , libslang.so.1 , libstdc++-libc6.1-1.so.2 , libvdkcompo.so.1 , libvdk.so.1 , libX11.so.6 , libXext.so.6 , libXi.so.6 , /bin/sh , libc.so.6(GLIBC_2.0) , libc.so.6(GLIBC_2.1) 
provides
libvdkcompo.so.1, libvdkcompo.so.1(GCC.INTERNAL), libvdkgnome.so.1, libvdkgnome.so.1(GCC.INTERNAL), libvdk.so.1, libvdk.so.1(GCC.INTERNAL), lexmarkz52
distribution
(none)
vendor
Lexmark International, Inc.
packager
(none)
build-time
Mon 17 Sep 2001 12:44:59 PM EDT 
base
/
filename
/home/Myname/ lexmarkz52-1.0-4.i386.rpm

One or two items seemed hyperlinked but they didn't take me anywhere when I clicked them so...can anyone tell me am I to remedy this?

---

### Post by FuturePilot on 2008-02-07
Ubuntu does not use .rpm packages. Instead it uses the Debian (.deb) packages. You could try converting it with Alien. Though Alien isn't really meant for converting drivers, but if there's no other option it might be worth a shot.
```
sudo apt-get install alien
sudo alien -c package.rpm
```

---

### Post by Thelasko on 2008-02-07
Lexmark is funny about not using standardized drivers.  Trying to use standard drivers will make it difficult to do things like duplex etc. I don't recommend using their printers for that reason.  I think you are best off using the drivers that came with Ubuntu since I consider you lucky the printer works at all.  

That being said I have gotten their(proprietary from Lexmark) drivers to work in Linux.  They give you the files in .rpm format which is for Red Hat or Suse Linux.  To make them work in Ubuntu you have to convert them into .deb format.  To do that you have to use a program called Alien.  Install Alien from Synaptic and  open the terminal and type:

```
sudo alien nameoffile.rpm
```

replacing "nameoffile" with the name of the file you are trying to convert.  You should be able to install the .deb file from there.

---

### Post by stchman on 2008-02-07
I agree with Thelasko.

Lexmark is notorious about not supporting Linux.  I recommend HP printers.

Do consider yourself lucky that that Lexmark printer works at all.  Lexmark has a lot of paperweight printers under Linux.

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z52](http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z52)

---

### Post by rustyDusty on 2008-02-07
I did as you both said.

The lexmark package was converted and the installation went smoothly.

This is what it said:
> Lexmark Z52 Printer driver
This package contains a printer driver for the Lexmark Z52 printer. It also contains a Graphical User Interface (GUI) utility named lexmarkz52 and is located under /usr/local/lexmark/z52/ directory. This utility can be used to determine the paper size, paper type and print resolution for your print job. It can also be used to perform cartridges operation on the printer. Requires: enscript >= 1.6.1 Requires: ghostscript >= 5.50
(Converted from a rpm package by alien version 8.68.) 

Now I opened a document and pretended to print but the print interface wasn't very different. I mean I had no options to print on both sides of page.

Maybe I need to reboot for changes to take place?

---

### Post by forrestcupp on 2008-02-07
It's pretty likely that all of those features aren't supported at all in Linux.  I have a Lexmark All-in-One X5150.  I can only get it to print.  The scanner is not supported.

---

