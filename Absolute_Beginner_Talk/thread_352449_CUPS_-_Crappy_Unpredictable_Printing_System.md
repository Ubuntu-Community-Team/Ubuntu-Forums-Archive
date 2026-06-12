---
title: "CUPS - Crappy Unpredictable Printing System"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Busta999 on 2007-02-03
Well at least on Ubuntu Dapper.

After a 3rd complete OS re-install on 2 differect computers I can confirm that CUPS is truly totally crap!!

It is totally flakey and completely defies logic as to what works and what does not.

As a twenty year IT professional veteran I have never encountered something so totally random as this implementation.

I have managed to get it working, well sort of, at times.

I once had it so that a pc running XP could use a printer on Ubuntu, with [http://farmer:631/classes/laser](http://farmer:631/classes/laser)  whoo whoo, of course the http:/farmer:631/printers/scx4200 never worked, neither did ipp from a MAC. But after 40 hours of methodical trial and error I got printing working through Samba, but not without the XP boxes complaining that we did not have access, while the Ubuntu bax was printing.

The most reliable way of making CUPS to work was waving the Ubuntu install disk over the monitor while chanting - 'make the printer work, make the printer work'. Now this only work one time in a hundred which while low it offered a more reliable way than using the web admin interface to CUPS which everytime it was used stated 'please wait while the service is restarted' swiftly followed by 'Unable to connect'. Then you try the old  /etc/init.d/cupsys restart, which sometimes works, if that fails then back to uninstall and then re-install the CUPS and the printer and start again.

Back to the cd waving only another 50 times around the monitor and printing will work again.......

Oh what a devious plan to wrench the masses away from MS.

Ah venting is so cleansing

Bring on the flamers

---

### Post by kwaanens on 2007-02-03
Actually the right abbreviation is Can't Usually Print Stuff :)
Sorry, I can't help!

---

### Post by jingo811 on 2007-02-03
Well there are two kinds of ppl in the world those who let out their fury in total outrage.  And then there are those who keep it inside themselves and go shoot ppl on the street. /(from the movie Anger Management)
Luckily no one is gonna get shot tonight ):P 
You might not know it but your complaining just saved 1.000.001 human beings from 40 hrs of wasted trial-n-error.  That's like 40.000.040 hrs total, give or take 4.500 years of wasted working capacity.  You just did humanity a big favour there!  That is if you really did your homework correctly, maybe you should compare notes with ppl with **pin-pointed questions** instead?

At least you made me more alarmed about trying out the CUPS on my home networking printer thus saving me 40+ hrs of reading and troubleshooting.
Maybe you should give [LPD]("http://en.wikipedia.org/wiki/Line_Printer_Daemon_protocol") a try it worked flawlessly when I tried it on my Windows XP before migrating to Linux. 

However I too must do some complaining about LPD working directly under Ubuntu it also is unpredictable compared to when using LPD under Windows XP.
In Windows you didn't need to have the printer boot at the same time as when the computer booted up.  But in Ubuntu that's almost a must in order for Linux to recognize a printer.
That's crazy!

---

### Post by Busta999 on 2007-02-03
Well bugger - ooops

I got CUPS working, at least from the point of view that XP and MAC users can print over ipp.

I mean print as in what they send to the printer gets printed.

The moany niggling things like XP frequently showing the printer as unavailable, it still prints.

As long as I don't actually use the GUI web Admin it works, The GUI Admin currently shows CUPS as NOT sharing published printers, kinda comical as the printer vmoits page after page of remote printing.

Also worthy of note - do NOT under any circumstances use the GUI ADMIN - it really bollocks up the CUPS!!!!!!

Play safe and edit the files.

To be really safe, take the drive out, open it and edit the file using a magnet, but don't forget when it works to give thanks to the CUPS gods for their infinite mercy.

Hey - what I love about all this stuff is the BUZZZZ when something works, its addictive!!!

---

### Post by pseudonym on 2007-02-03
You seem to have only mentioned the CUPS web interface, but what about GNOME CUPS Manager? (I'm assuming you use GNOME). It's never given me any trouble, though I don't have a networked printer admittedly (when I did, I edited the config files, but I didn't have GNOME CUPS manager installed anyway).

FWIW, in the past I had to hop clockwise five times around my printer, on my right leg, then five times counter-clockwise, on my left, on a night when there was a full moon, for CUPS to play properly. But I guess my kharma must have been different to yours. :)

---

### Post by Shay Stephens on 2007-02-03
I know this doesn't help any, but I have been using cups to print from my computer to another ubuntu computer with a printer.  It has never given me problems.  I used this guide to get it working:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

My computer is the client and the computer that has the printer is naturally the cups server.

---

