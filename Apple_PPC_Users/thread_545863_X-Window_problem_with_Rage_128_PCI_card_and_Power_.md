---
title: "X-Window problem with Rage 128 PCI card and Power Mac 9600"
date: 2007-09-08
forum: Apple PPC Users
---

### Post by MJMullinII on 2007-09-08
OK.

I just installed Ubuntu 6.10 for PPC on my trusty Power Mac 9600.  I first tried installing 7.04, but that is another story I may get to later.

ANYWAY, the install of 6.10 went beautifully.  Everything clicked and hummed right along.  When it restarted, however, the first thing I saw was that X-Windows was refusing to startup.  However, the operating system is running perfectly.  In fact,. I've already updated it with apt-get to the most recent packages and it flies (I have a 1 GHZ G4 upgrade in the machine with around 608 MB of RAM)

However, I am still unable to get X-Windows to start.  For those who don't know this particular Mac, it was the last to have 6 PCI slots.  It does this using a bridge.  My first thought was that maybe the  this confused the installer and it didn't assign the correct PCI location to it (i.e. PCI : ? : ?:?)

However, checking LSPCI, it did.  My only other thought is my monitor.  I have a AL2002W  LCD VGA/DVI digital flat panel.  The VGA connector is connected to the Rage 128 card in my 9600 and the DVI connector is connected to my Mac Pro.  It has a button on the front to switch between the two connections.  The LCD has a default resolution of 1680 x 1050.

Now, the installer correctly determined the name of my monitor, HOWEVER it tried to assign it a 1280 x 1024 resolution.  When I reconfigured X-Windows, I selected the high 1680x1050. (However, it doesn't work when set to 1280x1024 either)

I do not consider myself a complete newbie, but I'm not completely Linux experienced either.  I feel in my gut that it is something simple I'm overlooking, but it is escaping me.  I look forward to any help offered.

P.S. I'm more than happy to supply whatever details you wise older Linux people might request to further your diagnoses :).

---

