---
title: "PowerBook 180"
date: 2011-01-23
forum: Apple Hardware Users
---

### Post by crip720 on 2011-01-23
Hi.  I have an old Mac PowerBook 180 laptop.  The computer still turns on but the OS on the floppies will not boot up.  Was wondering if it is possible to load a linux distro on this computer, or is it a paperweight now.  Thanks Colin.

---

### Post by 1clue on 2011-01-23
That's a REALLY old computer.

[http://mac.linux-m68k.org/](http://mac.linux-m68k.org/)

IMO it's a paperweight.  You could get Linux working on it if you really wanted to (assuming no hardware problems), but you won't have an ubuntu-esque desktop.

---

### Post by crip720 on 2011-01-23
Thanks,  figure as much, main problem would be installing on it , think it only  has floppy drive?  Modem unknown/maybe.  Colin.

---

### Post by 1clue on 2011-01-24
Main problem is booting on it.

The status according to that site is that you won't get much of anything on there.  

[http://mac.linux-m68k.org/status/MAC_MODEL_PB180.php](http://mac.linux-m68k.org/status/MAC_MODEL_PB180.php)

No apple desktop bus (which may or may not include built-in keyboard) and no floppy drive, and no scsi.  The only thing that works is the serial port.  Some things to ponder:
[LIST=1]
[*]I have exactly 100 times as much RAM as that thing had hard disk space if you got the largest drive available.
[*]Gnome terminal on my system right now is taking more than 13 mb.  The maximum supported RAM in your system will hold that, barely.  No operating system, just the GUI version of the terminal.  Firefox is taking 204 mb right now.
[*]A standard terminal, without X, takes around 4 Mb last I checked.
[*]Best case scenario, I think you might get one terminal up, no X, basically the setup you would get if you loaded Ubuntu Server off of a CD-ROM, before you install.  If you had a CD-ROM.
[/LIST]

FWIW if you're just doing it because you're bored and want a challenge, then maybe pursue this further.  If you want something to be useful then that machine stopped being practical over 10 years ago.

I know there are a lot of people who say Linux is the fastest, least CPU-intensive operating system you can load on any computer, but that's essentially a myth.  It's theoretically CLOSE to true if you install a minimal command line environment with no X and not much else either, but not if you're loading something like Ubuntu.  You turn on all the fancy effects and you're using more resources than any Microsoft OS ever did.

My advice is to go buy a motherboard, an enclosure, a CPU, a drive and whatever else you need and start making a brand new box.  That's real fun that gives a real reward at the end of it.

---

### Post by linuxopjemac on 2011-01-24
Wow, this is challenging :) Good luck. I personally never tried it on these kind of machines. My knowledge reaches PowerMac 7600 and the like. This is even older.

---

### Post by SarahKH on 2011-01-24
Theoretically you could get Linux on the PB180, all the oddities already listed aside.  

However the thing is so old I'm not sure how useable it would be.  Considering even an ancient Celeron powered EEE PC 701 netbook would run rings around the old 68k CPU in there I think you'd be stuck at text only. 

Actually, there's a nifty project, find a cheapo netbook with roughly the right dimensions and combine the PB's shell with it's innards.

---

