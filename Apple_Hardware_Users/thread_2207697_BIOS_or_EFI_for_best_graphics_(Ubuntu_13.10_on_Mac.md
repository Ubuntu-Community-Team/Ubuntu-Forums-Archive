---
title: "BIOS or EFI for best graphics? (Ubuntu 13.10 on MacBook 5,1 w/ NVIDIA GeForce 9400M)"
date: 2014-02-24
forum: Apple Hardware Users
---

### Post by Brighid on 2014-02-24
Hi all!  I recently got back into Ubuntu after being away from it for a long time (I will admit that Steam's arrival on Linux was a big factor for me!).  Which brings me to my question .. after seeing how poorly DOTA 2 ran on my MacBook in OS X Mavericks, I thought I'd try a different OS.  Running the game in Ubuntu 13.10 (in BIOS legacy mode) with the NVIDIA drivers (the default drivers couldn't even render anything!) gave beautiful results, especially in comparison with OS X (not to say the FPS is great just yet - I'll have to play with the settings).  Still, I have read that running Ubuntu in EFI or BIOS mode can change things, but I'm not sure if it would be for the better or not.  There seems to be a lot of ambiguity.

So, in short, am I getting the best graphics I could possibly get with Ubuntu in BIOS mode (does anyone know)?  Or would switching to EFI improve things?  Of course, I could try both setups and find out for myself (and I might), but I thought I'd see if anyone else had any thoughts.

If it helps, my MacBook is using an integrated card, the NVIDIA GeForce 9400M (speaking of which, does anyone know if it's possible to increase the amount of RAM allocated to the card, since it shares it? when in Windows XP, for example, it uses 512MB instead of 256MB, like OS X does).

Thank you in advance for any help. :)

---

### Post by jorgeblasio on 2014-02-25
Check this out:

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by Brighid on 2014-02-25
> **jorgeblasio said:**
> Check this out:

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

In my seaching I had found this page: [http://www.rodsbooks.com/ubuntu-efi/](http://www.rodsbooks.com/ubuntu-efi/)  On it Rod talks about some of the disadvantages of using EFI mode, which is why I'm hesitant to try it out myself.  The Nvidia drivers seem to be working pretty well for me in BIOS mode.

Rod also linked to the page you suggested, and I had read around on there some, too, but there aren't any comments specifically (that I saw?) on graphics - only that Macs with two graphics cards could choose which one to use (I only have an integrated card so that's moot).  Thank you for the suggestion, though.

---

### Post by jorgeblasio on 2014-02-26
Why don't you try a liveUSB under EFI mode?

---

### Post by Brighid on 2014-03-19
> **jorgeblasio said:**
> Why don't you try a liveUSB under EFI mode?

Hm, I may try that.  I had also realized that maybe using a different "flavor" of *buntu might work, too.  For now, though, BIOS mode is working beautifully and I don't want to fix what isn't broken.  It's not a super high priority as I don't play too often, mostly a curiosity, but if anyone else is exploring this too please post any ideas!  If I come back to this I'll be sure to update this thread.

---

