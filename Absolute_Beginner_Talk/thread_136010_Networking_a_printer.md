---
title: "Networking a printer?"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-02-25
I'm using Breezy and the other machine is running Windows XP Pro.

We are networked in that I can see the XP machine and read/write to its fat32 partition.

How do I share my laserjet 4 Plus on LPT1? 
If it matters I am using the ljet4 driver - only one that seems to work although it prints an extra blank page each time)

---

### Post by Pragmatist on 2006-02-26
Which machine is the printer attached to? Are you using KDE? GNOME?

---

### Post by _simon_ on 2006-02-26
printer is attached to my pc running breezy (GNOME)

---

### Post by ape on 2006-02-26
There are a number of different methods you can use:

1. You can install Samba on your Breezy box and share the printer to the WinXP machine that way.

2. Install standard lprng on your Breezy box and just look like any other UNIX lpd server to your WinXP box.

3. Install some combination of cupsys (and cupsys-bsd I find) on the Breezy box and from the XP box connect to the printer as an IPP printer. (outlined in the first link below).

Some links:

[http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html](http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html)

[http://www.xml-dev.com:8080/tldp/http://cvsview.tldp.org/index.cgi/*checkout*/LDP/howto/docbook/Debian-and-Windows-Shared-Printing/Debian-and-Windows-Shared-Printing.xml](http://www.xml-dev.com:8080/tldp/http://cvsview.tldp.org/index.cgi/*checkout*/LDP/howto/docbook/Debian-and-Windows-Shared-Printing/Debian-and-Windows-Shared-Printing.xml)



Good luck!

---

