---
title: "Xubuntu 6.06 printer doesn't show up"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by PolarisNC on 2006-07-24
[FONT="Arial"]I just recently installed xubuntu 6.06 (via alternate install cd) on my pet dinosaur (PII 350 mHz, 128 Mb ram).

Everything works fine (albeit slowly) except that no printers show up in *Accessories-Print Manager*, and clearly, any attempt to print has No Effect At All.

The printer in question is an HP Deskjet 3745,connected via USB.

Stuff I've already tried:

restart CUPS

check synaptic package manager for updates to HPLIP (version listed is 0.9.7)

chat with HP technician - couldn't help, but pointed me to [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/), which lists my printer as working under version 1.6.6a

downloaded hplip-1.6.6a.tar.gz, and attempted HP's manual install, but ran into problems around step 3:
[/FONT]
[FONT="Courier New"]dan@Hex:~/documents/hplip-1.6.6a$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
dan@Hex:~/documents/hplip-1.6.6a$
[/FONT]
[FONT="Arial"]Granted, I don't know which of these responses are good, and which are bad, but the line
[/FONT]
[FONT="Courier New"]checking whether make sets $(MAKE)... no[/FONT]
 
[FONT="Arial"]seems to be a problem, since the next two steps involve that command, and the terminal doesn't seem to know what to do with them.
(the specific page with their instructions:  [http://hplip.sourceforge.net/install/step3/index.html](http://hplip.sourceforge.net/install/step3/index.html))

Any suggestions as to what I need to do will be appreciated.[/FONT]

---

### Post by encompass on 2006-07-25
Look more simply at the issue at hand.  Did you try manually adding the printer.  The driver, odds are, is already in the system.  I can't remember how to add a printer in xubuntu, but in gnome it is System--- administration--- printers
There should be something similar in xubuntu.
In addition, make sure the printer is on, and that all cables are connected and not plugged into hubs.  This helps aliminate problems in the setup.
I can help you more if these don't work.  I have xubuntu at home.

---

### Post by Sef on 2006-07-25
> dan@Hex:~/documents/hplip-1.6.6a$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
dan@Hex:~/documents/hplip-1.6.6a$

Build-essential needs to be installed to compile.

Open a terminal

sudo apt-get update

sudo aptitude install build-essential

Note: you may replace sudo with something more appropriate for xubuntu.

---

### Post by encompass on 2006-07-25
[http://localhost:631/admin](http://localhost:631/admin)
in your browser...
add a printer there... perhaps that should do it...Hope it helps... otherwise I am lost.  Making a new driver won't work unless you have cups playing with it.](*,)

---

### Post by VirtuAlex on 2006-07-25
I remember when I tried to connect my deskjet ubuntu did not list any usb ports available. Somewhere I found suggestion if I remember it correct load ubuntu, unplug the printer, plug it again, and then restart computer. After this magic it appeared in the list when I clicked "New printer." Have no idea why this simple procedure worked for my printer...

---

### Post by PolarisNC on 2006-07-25
> **encompass said:**
> [http://localhost:631/admin](http://localhost:631/admin)
in your browser...
add a printer there... perhaps that should do it...Hope it helps... otherwise I am lost.  Making a new driver won't work unless you have cups playing with it.](*,)

OK, tried that one, and got

401 Unauthorized

Enter your username and password or the root username and password to access this page.

(my login/password works fine for other administrative tasks)

o_O

EDIT:  [http://localhost:631/admin](http://localhost:631/admin) shows the printer twice, as

HP Deskjet 3740 (HP Deskjet 3740 USB #1)
and
HP Deskjet_3740 (hp:/usb/Deskjet_3740?serial=CN48V150V9040Q)

trying to add the first gets me the 401 Unathorized message
trying to add the second gets me a repeated request for username/password, then a blank white screen
:confused:

---

### Post by hellowood on 2006-07-27
Have you add your cupsys into shadow group?

---

### Post by PolarisNC on 2006-07-27
> **hellowood said:**
> Have you add your cupsys into shadow group?


AHA!

Done, and done!


thanks, everyone!

Polaris

---

### Post by TuxCrafter on 2006-07-27
[http://www.ubuntuforums.org/showthread.php?t=170342&highlight=xubuntu+cups](http://www.ubuntuforums.org/showthread.php?t=170342&highlight=xubuntu+cups)

---

