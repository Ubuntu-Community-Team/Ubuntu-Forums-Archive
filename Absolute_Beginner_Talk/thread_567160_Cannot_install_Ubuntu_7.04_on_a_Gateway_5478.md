---
title: "Cannot install Ubuntu 7.04 on a Gateway 5478"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Malleus Dei on 2007-10-04
I'm trying to install Ubuntu as a dual boot option in a new Gateway 5478 computer. Specs are Core 2 Quad, Q6600,  2.4 GHz, 1066 MHz FSB, 2 x 4 MB L2 cache, 4 GB of PC2-5300 (667MHz), 2 x WD 500 GB SATA-300, Windows Vista Home Ultimate (yes, I know, I know, but the wife wants the media center).

I've done maybe a dozen 7.04 installs before this, both regular and dual-boot, desktop and laptop, and none of them have ever been the slightest problem. This one is. It fails on install attempts from both the regular and alternate install CD with the message "/bin/sh: can't access tty; job control turned off." My first thought was that the problem must be the DVD/CD-ROM drive, so I whipped out the Ubuntu 7.04 install I keep handy on a 2GB flash drive, plugged it  in, told the 5478 to boot from it, and got the plain and simple error message "Boot failure." The MBR on the flash drive was fine - I checked.

So is the hardware in the Gateway 5478 just not supported by Ubuntu 7.04? Or is there another problem entirely?

The only alternative apparently available to me appears to be installing another Linux distribution, which I'd definitely rather not do unless there is no other choice. Does anyone know what is going on here? Can anyone help? I'd really like to stay with Ubuntu.

---

### Post by drsmaw on 2007-10-04
Malleus,
Just try another distro to see if you encounter the same problems.  I personally have done that to narrow down problems and it works mos of the time for me.  Even if you use something light like DSL(50mb) you can't go wrong. Or even try PCLinuxOS2007, just to see if it will accept it.
But as always, some things are right in front of our face, re-trace your steps - maybe u missed something.
Sorry, that's all I can help with.  But at lease someone answered your post, I hate when no one answers.

---

### Post by koma77 on 2007-10-04
Seems like this has happened before:

[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

Also, I would try to install 6.10 or perhaps 7.10 (beta at the moment) to see if there is any difference.

And then toy around with common boot options for nasty laptops. (Don't know them by heart, sorry)

---

### Post by Malleus Dei on 2007-10-04
Thanks for the advice! I have tried two other Linux distros on this machine and they both choked. Debian wouldn't even boot; openSUSE got to the third (the actual install) screen and then just sort of slowly died out. Just for grins, I even tried to see if XP would install but consistently got the Blue Screen of Death. This machine appears to take nothing but Vista. Argh.

I'm downloading the 7.10 beta right now and will try to install it and report back. If/when that fails I will try Red Hat.

Needless to say I am not optimistic at this point. Thanks for the advice.

---

### Post by odzk on 2007-10-04
hmm thats odd. maybe they put something on the hardware side like an program in motherboard or something that will not permit other OS install aside for vista.

hehhee maybe linux community is getting popular, and microsoft is getting more cautious about it. ^^

---

### Post by Malleus Dei on 2007-10-04
7.10 won't install either. I get the opening screen up but it will go no farther.

Anyone have any ideas?

---

### Post by drsmaw on 2007-10-05
Sometimes it can be the quality of cd-r you're using to burn the iso.
Did you lower the write speed?
check md5sum?
try the same cd on another computer, see how it reacts.

---

### Post by drsmaw on 2007-10-05
come to think of it, I ran into the same problems when trying to get Pclinuxos running.  it would get to the start screen and then nothing. I recently wiped my HDD which had Vista on it, and everything went through no poblem on 4 different distros.
Maybe Vista is in the way somehow.
I am MS free for a month now, and have not turned back.

---

### Post by arkhitekton on 2007-10-14
Some information, unfortunately not a solution.  I tried to install 6.06, 6.10 and 7.04.  I could not get any to install.  I did get SUSE 10.1 to install but it did not detect the Ethernet adapter.  I plugged in a Linksys USB Ethernet adapater and it saw that immediately.

Interestly when I attempted to re-install Vista it could not see the Ethernet adapter either and I had to plug in the USb Ethernet adapter and install the drivers.  Then download the drivers for the onboard Ethernet adapter from Gateway.  But that's why we like Linux I suppose?

---

### Post by Malleus Dei on 2007-10-16
> **drsmaw said:**
> I recently wiped my HDD which had Vista on it, and everything went through no poblem on 4 different distros. Maybe Vista is in the way somehow.

That's what I am thinking. I'll buy a new hard drive and try a Vista-free install this weekend.

---

### Post by Malleus Dei on 2007-10-16
> **arkhitekton said:**
> Some information, unfortunately not a solution.  I tried to install 6.06, 6.10 and 7.04.  I could not get any to install.  I did get SUSE 10.1 to install but it did not detect the Ethernet adapter.

Good job, I couldn't get SUSE 10.1 to install at all. Why would the Ethernet adapter go undetected? New kind of BIOS?

If anyone else has any ideas on how to install Linux on this box I sure would appreciate reading them.

---

