---
title: "Lexmark Z65 trouble..."
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by starcraft.man on 2007-03-08
I want to get my Lexmark Z65 printer, I tried using CUPS but it doesn't have drivers for my exact model and recommending I install Z11 (didn't work ><). Does anyone else have a Z65 and can tell me how to make it print properly? It is a kinda old printer I imagined it would have been done already...

Help greatly appreciated. :)

---

### Post by wpshooter on 2007-03-08
Are there driver(s) that are built into Ubuntu for this printer ?

If so, did you try ALL of the listed ones for this printer ?

However, having asked that, it seems to me that I may be remembering a prior post regarding this same printer and if memory serves me correct, I am thinking that maybe there are NO Linux drivers for this particular printer.  But don't take that as gospel.  Do some looking around.

Good luck.

---

### Post by klytu on 2007-03-08
> **starcraft.man said:**
> I want to get my Lexmark Z65 printer, I tried using CUPS but it doesn't have drivers for my exact model and recommending I install Z11 (didn't work ><). Does anyone else have a Z65 and can tell me how to make it print properly? It is a kinda old printer I imagined it would have been done already...

Help greatly appreciated. :)

[_This thread_]("http://www.ubuntuforums.org/showthread.php?t=14546&highlight=z65") may be helpful. A poster in the thread also wrote a pretty good howto [_here_]("http://www.ubuntuforums.org/showthread.php?t=49714&highlight=z65").

---

### Post by starcraft.man on 2007-03-08
> **wpshooter said:**
> Are there driver(s) that are built into Ubuntu for this printer ?

If so, did you try ALL of the listed ones for this printer ?

However, having asked that, it seems to me that I may be remembering a prior post regarding this same printer and if memory serves me correct, I am thinking that maybe there are NO Linux drivers for this particular printer.  But don't take that as gospel.  Do some looking around.

Good luck.

ya, I tried all the printer drivers that were close enough... Now I dont seem to be able to see the USB printer connected anymore? I glanced over a command before to show all the USB connected devices in Terminal, can someone tell me what it is? 

Oh and I was looking around Lexmark and apparently they made a Linux driver for it for a few different buissness versions of Linux like Red Hat and Mandriva, can I use one of those? They close enough? They also use CUPS right?

[HTML]http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=37:1:0:340:0:0[/HTML]

---

### Post by doubtful wisdom on 2007-03-09
Problem may be to recent update.  Lost printing capability on my Epson CX6600 after updating yesterday.  I did see a work around, but do not understand how to implement it, as all of this is quite a mystery to me.

---

### Post by msak007 on 2007-03-10
> **starcraft.man said:**
> ya, I tried all the printer drivers that were close enough... Now I dont seem to be able to see the USB printer connected anymore? I glanced over a command before to show all the USB connected devices in Terminal, can someone tell me what it is? 

Oh and I was looking around Lexmark and apparently they made a Linux driver for it for a few different buissness versions of Linux like Red Hat and Mandriva, can I use one of those? They close enough? They also use CUPS right?

[html]http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=37:1:0:340:0:0[/html]
Do _**NOT**_ try the drivers from Lexmark's site! I foolishly tried that once and almost hosed my system and couldn't install any software. They only offer it as an RPM, and you would have to use alien to convert it to a .deb and install it. Last time I tried that, apt got messed up (more details in [this]("http://www.ubuntuforums.org/showthread.php?t=39563&highlight=z65") thread). Could've been a problem with alien, but my advice is to stay away.

I have one of these printers (bought long ago, before switching to Linux) and after trying to get it working I learned one thing - Lexmark has crappy, practically non-existent Linux support. They're up there on the list of hardware vendors from whom I will not buy any hardware in the future. I know that's not what you wanted to hear, but unfortunately your printer will not work in Linux. It's a shame because that's one of the best printers they ever made (I used to be a sales rep for them) and one of the best I've used. If you stumble on a way to make it work, please let me know. Otherwise I'm in the market for a new printer, and it will most likely be an HP or an Epson (Canon's support is useless as well).

---

### Post by Jani97 on 2007-09-07
Hi,

Check my reply dated 7 september, 2007 here [http://ubuntuforums.org/showthread.php?p=3327721#post3327721](http://ubuntuforums.org/showthread.php?p=3327721#post3327721) for how i got my Lexmark Z65 working with the SUSE 10.1 driver on Feisty Fawn

/Jani

:D:D:D:D:D

---

### Post by anargyros on 2007-12-10
Hi 

Yes, I have managed to install the Lexmark Z65 drivers under Ubuntu 7.10 Gutsy. Initially  tried to download the drivers from Lexmark, but that did not work .. for some reason, Then I downloaded the drivers from the above site : 

wget [http://www.downloaddelivery.com/srfi...S-1.0-1.TAR.GZ](http://www.downloaddelivery.com/srfi...S-1.0-1.TAR.GZ)

and followed the instructions. I installed the deb packages using "dpkg -i" as opposed to alien (after I converted to deb using alien).

The new install works just fine ...

many thanks
anargyros

---

