---
title: "G3 iBookk assistance for newbie"
date: 2010-08-06
forum: Apple Hardware Users
---

### Post by danpwright on 2010-08-06
Dear all,

First of all, I am veery excited about Ubuntu.  Long time mac user, sometimes Windows user (for work) and am delving into Linux now.

So...I have an iBook G3 700 Mhz with an airport card.

Ubuntu 10.0.4 install went perfectly; however, I have a wireless issue that isn't solved by the recent thread on here; a new problem.

Old problem that others have had and I also have:

Can see wireless networks but can't connect.  I have changed my router to running WEP instead of WPA as the original airport cards don't support it.

Have tried:

Switching from Network Manager to WICD.  No luck.

On the offchance, the Broadcom driver download suggested in the PPC wiki.  No luck.

Trying the most recent "agere" move; when I try the command (from the previous thread) I get "No such file or directory".

Stuck!

Would love to move onto Ubuntu but no wireless is a sticking point for me.

I would like either suggestions of what to do OR a suggested flavour of Linux that will definitely work.  Tried Yellow Dog, same problem.  Tried Debian (but got stuck once I have done an install and just had a command line rather than a GUI: I don't know command line yet!).  

Any and all help much appreciated.

Dan Wright

---

### Post by linuxopjemac on 2010-08-07
I can help you setup Debian Mint LXDE, which runs smoothly on your machine.

[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)

---

### Post by bprins on 2010-08-07
you can see a network to connect to?
the broadcom proprietary driver is activated?
tried to turn off any kind of encryption on your router and try to connect then?
iwconfig gives output that makes sense?
lspci | grep Broadcom lists your device?

---

### Post by danpwright on 2010-08-08
I can see a network to connect to; it just asks for the passphrase over and over.  

I have other computers on my network connecting to my router, so working without encryption is a non starter.  

I have no idea what iwconfig should look like when it makes sense...any help? It does say 'Power management off" but can see networks, so must be a driver issue.

lspci | grep Broadcom lists nothing.  I believe my airport card is one of the original ones, and a solution was offered here but I tried typing the command and nothing worked;

[I]"The original airport card (lucent/agere Orinoco) did NOT work out of the box and kept asking for wireless keys.

I eventually installed Debian Lenny (5.04) PowerPC XFCE + LXDE nCurses installer. It worked with keys and wireless IDs entered during installation. Yet while rutilt could see wireless access points, it kept complaining that it couldn't load the keys. I'm not sufficiently proficient with the CLI and the concepts of wpa_supplicant to make it all go from the command line, nor do I care that much (OK, lies... I could do it but it required tedious mucking around with /etc/network/interfaces and much ifups and ifdowns). I broke the system mixing testing with Lenny while trying to install wicd (don't ask how; I don't know).

So -- thanks to y'all, I had confidence that a reinstall of Lucid would work and now I'm happily back in the fold.

Only particularly goofy thing -- had a few errors on first reboot. No nm-applet showing on 2nd reboot. Works like a charm on 3rd reboot. Go figure.

Just do as the nice man said:

sudo mv /lib/firmware/agere_sta_fw.bin /lib/firmware/agere_sta_fw.bin.bak ; sudo pccardctl eject ; sudo pccardctl insert

reboot reboot reboot

THANKS TO ALL OF YOU!

...CirdanLeVancien..."[/I]

So...I have no idea if I should have downloaded a driver for the card I have, what to type...

I am learnign command line as I go, so I don't even know basics of it!

---

### Post by danpwright on 2010-08-08
How up to date is Debian Mint?  That looks easy to setup...but I wonder if I will hit the wireless card issue again...

---

### Post by linuxopjemac on 2010-08-08
Everything should work, the software is a little outdated (Iceweasel 3.0.6 for example)...But you will at least end up with a machine that works.

---

### Post by heluani on 2010-08-08
I'm surprised you mention issues with the wireless card and wpa. I'm running gentoo on a powerbook G4, admittedly a different machine, but I would've thought they use the same airport card. wpa_supplicant with the wext extensions is working fine with the broadcom sta driver. 

R.

---

### Post by danpwright on 2010-08-08
I am fairly lost...am going to try installing 9.10 Karmic Koala using the walkthrough on ComputerAnt to see if I can get that running; if not, I really don't know what to do now.

Have even tried installing Linux Mint and still can't get it to work...and yet in old Mac OS X.3, it works straightaway.

Sigh.  Pressing on.

---

