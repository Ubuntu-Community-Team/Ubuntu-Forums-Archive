---
title: "Two Soundcards - Problems"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-01-10
I've got a "sound card" built-in my motherboard, and I also have a regular sound card (chipset: EMU10k1). They were both detected out-of-the-box, and the MoBo one works perfectly.

I'm not sure about my SoundBlaster, though. Everything looks good, but when I plug my speakers into it, no sound comes out (I'm just using amaroK for testing). I've never had this situation before, so I'm not sure where to start. Fast facts:

-Volume Control recognizes both. The SB isn't muted and volume is turned all the way up.

-lspci | grep audio:

> 00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
01:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)

-They both use ALSA.

-I didn't install any drivers for either one of them. Right now all my sound drivers are purely out-of-the-box.

But I've read around that the EMU10k1 chipset works perfectly without any help. Is there a way to have audio through both, or choose which one I want (blacklist the MoBo sound or something)?

---

### Post by tonyr1988 on 2007-01-10
After some researching (I probably should have done that before posting, huh?), I solved it. In case others have this problem, here's what I did:

-Figure out the module name of the one you *don't* want. In this case, mine was snd_intel8x0 (use the command lsmod to see the modules loaded - try doing searching on it to narrow it down). For example, my Device Manager said it was using an Intel driver, so I tried: 

> lsmod | grep intel

and narrowed it down to the snd_intel8x0 module.

-Find the file with your blacklisted modules. You have to tell it to not load the module for the sound card you *don't* want activated. The places I saw had different files with blacklisting. I found mine through:

> locate blacklist

and saw that it was /etc/modprobe.d/blacklist.

-Blacklist it. Open the file (ex: sudo nano /etc/modprobe.d/blacklist), go to the bottom of the file, and add the module to the list. Not sure if different versions have different formats, but I added the line:

> blacklist snd_intel8x0

to mine (and a little #comment to remind me what I was doing :D).

-Reboot.

At least that seems to be working for me so far. Could someone let me know if I did it wrong?

---

