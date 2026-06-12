---
title: "no Gnome; no network"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by jim mcnamara on 2006-03-18
Gnome will not start, and there is no networking at all.  netstat -rn shows nothing.  I beleive I can start the network if I can get Gnome and mozilla going.  I have a network startup cd that runs only under a browser.

Any help is appreciated.

Start here maybe - shortened version of the X Window log:

> 
(edited to shorten)
X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux devbox 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
..............(deleted)
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
....(deleted)
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
.... (deleted )
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
.... (deleted)
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, 915GM
(II) Primary Device is: PCI 00:02:0
(EE) No devices detected.

Fatal server error:
no screens found



---

### Post by Steve1961 on 2006-03-18
[QUOTE=jim mcnamara]Gnome will not start, and there is no networking at all.  netstat -rn shows nothing.  I beleive I can start the network if I can get Gnome and mozilla going.  I have a network startup cd that runs only under a browser.

Any help is appreciated.

Start here maybe - shortened version of the X Window log:[/QUOTE]


Have you tried reconfiguring X?  If not try running sudo dpkg-reconfigure xserver-xorg from the command line and follow along.

---

