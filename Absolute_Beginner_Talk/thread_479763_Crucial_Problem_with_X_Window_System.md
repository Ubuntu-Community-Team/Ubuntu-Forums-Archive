---
title: "Crucial Problem with X Window System"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Rogue Agent on 2007-06-20
Recently I posted a problem I was having with my laptop freezing on me after upgrading to the newest version of ubuntu.  I decided to try  fixing it by using the Sticky about upgrading with ATI cards.  I did everything in the guide, but now have run into an even worse problem.  After rebooting, I come up with what seems to be the Ubuntu equivalent of the Blue Screen of Death.  A funky error message popped up and I wrote it down so I could reference it later.  Here it is:

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System:Linux jake-laptop 2.6.20-generic #2 SMP
Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure that you have the latest version
Module loader present
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log File: "/var/log/Xorg.0.log", Time: Jun 12 00:58:17 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected

I looked for some answers at the Xorg site.  Here's what I got:

It is very likely that your xorg.conf file doesn't contain the correct driver(s) for the chipset(s) in your system or that your chipset isn't supported by any of the drivers.
You can check for the detected devices in the log file (in most cases /var/log/Xorg.0.log) by looking for lines like:
(--) PCI:*(1:0:0) Neomagic Corporation NM2200 [MagicGraph 256AV] rev 32, Mem @ 0xfd000000/24, 0xfe800000/22, 0xfec00000/20
In this example the active video device (the one with the *) is a Neomagic NM2200 video chip. In order to get this chipset to work you'd have to use the neomagic driver.
If you are using a distribution you should rerun its configuration tool. If there is no such tool, or if it keeps configuring your Xserver wrong you may want to try xorgcfg, the graphical tool shipped with Xorg. You can also let the server generate a config file: as root just run X -configure.
Please note: If you appear to use the correct driver and you still keep getting this message it is very likely that your chipset isn't supported (yet). In this case you may try the vesa driver or - if this doesn't work - the vga driver. However both are entirely unaccellerated.

It's been a couple of days since I tried to follow the instructions, but I remember having trouble executing the commands.  I also got an error involving my AVG Antivirus.  I forget what step in the process of trying to use the Xorg instructions when it happened, but it said:

avgscan [5545]: ERROR: registration to Dazuko failed

I also had problems getting to into root.  I would also like to try the drivers talked about in the Xorg guide.  Any help with this at all would be greatly appreciated.  Thanks in advance.

---

### Post by Happy_Man on 2007-06-20
Oh, dear. First off, have you tried the command ```
sudo dpkg-reconfigure xserver-xorg
``` while booted into recovery mode?

---

