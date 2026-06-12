---
title: "installing ubuntu on hp tx1314"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by bebops_lost on 2007-12-20
help!
I am trying to install ubuntu on my new laptop (hp pavillion series tx1314ca) so that I can dual-boot with Vista, -but I am having huge problems with the video drivers.
the hardware is supposed to be Turion 64, though I've been warned that the computer only actually has 32-bit processor, and a 64 bit 'emulator.'So for that reason, I've tried installing both 32, and 64-bit versions of both feisty fawn and Gutsy gibbon, and I've also tried using the alternate cd of GG -everything failed.
So far, the furthest I've gotten is with the 32-bit gutsygibbon alternate cd. it installs fine from the text mode, and then when it comes time to boot up for the first time, after selecting the ubuntu partition to boot from  I see a brief text screen saying:

Starting up...
[0.612000] PCI: BIOS BUG #81[49435000] found

and then the ubuntu bar fills up, and then abruptly the whole screen goes crazy (sometimes it bleaches out white, other times it's just a grey mash of dots.)
I'm pretty sure it's not a conflict with Vista, since I get a prompt asking me which partition I want to boot from, and it seems clear that it's going into Ubuntu. 
I've had similar problems with the other versions even at the installation step, and the only reason this one got through installation (I think) is because of the text installation -but anytime it tries to go to the GUI the screen has a hissy fit. I don't really care if the tablet feature ends up working, but I have a suspicion that this display feature might be causing the problem. 
Any words of wisdom ?
thanks for any help you can offer.

---

### Post by kestrel1 on 2007-12-20
Have you tried using the Live CD?

---

### Post by bebops_lost on 2007-12-20
yes, I tried the live cd first.
Trying to boot up into ubuntu using the live cd caused the video to crash in the same way as described above (before I got the chance to try to install) as soon as it goes to the GUI it fails.

---

### Post by PinkFloyd102489 on 2007-12-20
Disable Plug and Play OS in your BIOS, then report back.

---

### Post by bebops_lost on 2007-12-21
*"Disable Plug and Play OS in your BIOS, then report back"*

I'm not sure what you mean: The BIOS screen that I go to at boot-up has a few options for setting the boot-order, and allocating memory, but I don't see anything about "Plug and play OS" -presumably you mean the settings for the operating system to kick in automatically (do you think that Vista is coming on?)
thanks

---

