---
title: "connecting to wirless internet PCI"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by nevadaman on 2007-08-28
It has been awhile but I want to thank all who responded to my previous questions.  I finally found a wireless internet PCI card supported by Linux.  I have installed it, unzipped and downloaded the Linux driver but for some reason I cannot connect to the wireless modem,or router. I don't know where I went wrong I have the "key" for the router but no workie.  I am running WinXP right now and the card is ENCORE ENLWI-G2.  I pick up my friends DSL using a D-link for windows XP in a Compaq desk top PC with no problem.  My 'Feisty Fawn" is installed on a second internal HD but I can't get on line.  Is there someone out there that could possibly be of assistance?  I am new to this stuff and do not understand all the abbreviations and phrases that are used so I need someone  that talks my type of English.  Another problem,  I am 75 years young and a little slow on learning new things  but I do have "pre-computer" electronic experience.                                                                                                 Thanx,  Nevadaman in NM

---

### Post by Mark_in_Hollywood on 2007-08-28
In any event, having checked out Encore's webpages, I see the driver for Linux. After you either: Open with Archive Manager (default) or Save(d) to disk, what did you do next as it is a .tar.gz file? Does that mean it has to be compiled? Sadly I don't know. Generally the commands are: sudo make, make clean, make install, etc. They may not be necessary here. You have to have the compiling software pre-installed.

How do you boot into the 2nd harddrive? From the BIOS? Well, OK. Once you have Feisty running, is there a gnome network manager icon on the top, right side of the panel. The panel has the date and time at the right, top side, or at least mine does. If you have a net icon, right click it, if you see "enable wireless" without a check-mark in front of it, click it and put a check mark. Maybe reboot after that, but give it a bit. If there is only a "Enable Networking" checked, click it, once the next "window" comes up, look for the Wireless part. You should be good to go from there. 

I just installed wireless for the 1st time about 6 weeks ago. What a pain in the butt. My card is a D-Link WDA 2320. (PCI). I had to transfer my entire /home folder, reinstall Feisty and xfer the /home back, etc. It did work immediately upon the re-install, however. That card uses Mad WiFi drivers, built into linux-kernel. Sorry, I'm getting off topic.

As for being 75 and not up on acronyms, I'm in my 60s and not much better off. DHCP? TCP stack, ABCDEFG . . . what's with that stuff?

---

