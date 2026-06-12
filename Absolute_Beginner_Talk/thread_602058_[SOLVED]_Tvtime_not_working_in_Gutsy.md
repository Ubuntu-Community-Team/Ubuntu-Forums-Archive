---
title: "[SOLVED] Tvtime not working in Gutsy"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by wayfarer51 on 2007-11-03
Tvtime worked fine in Feisty.  All I did was install Tvtime, plug my Hauppauge WinTV USB2 (NOT a GO, NOT a PVR, NOT a Nova) into a USB port, run Tvtime and I was watching TV in a matter of minutes.

Then I upgraded to Gutsy.  I'm really regretting it.  Tvtime now gives me a blue screen and "No video source", "No signal", "Message too long, cannot open capture device /dev/video0".  So i'm screwed out of watching Heroes.

I've tried uninstalling/reinstalling Tvtime.  If there're posts in other places in these forums that seem to even bear a *distant* relationship to this problem...I've tried all the suggestions in them, to no effect.

I've got an ATI Radeon X300 RV370 card in a Dell Dimension.  If a responder needs more info, I'll get it for you.

If anyone could help me out, I'd be eternally grateful.  I just need to know what Sylar's doing.

TIA

Neill Dumont

---

### Post by Jose Catre-Vandis on 2007-11-03
Check your dmesg after you insert your TV adapter, this should tell you the device and its location. You will probably need to edit the tvtime xml file and change /dev/video0 to whatever you find?

---

### Post by wayfarer51 on 2007-11-05
Nope...dmesg produced /dev/video0

---

### Post by Jose Catre-Vandis on 2007-11-05
Is your card being loaded properly?

Do you see "UNKNOWN/GENERIC" in dmesg, or the name of your card?

If you see the former you will need to identify the card and tuner numbers and enter these in. Gutsy should do this, but might not be?

---

### Post by wayfarer51 on 2007-11-05
Alas, it shows:

[   30.127038] tveeprom 0-0050: Hauppauge model 42012, rev C186, serial# 2828640

and it is a Hauppauge WinTV USB2 tuner

---

### Post by Jose Catre-Vandis on 2007-11-05
what is the chip onboard? (e.g. bttv/saa7134/cx88 )

---

### Post by dixonstalbert on 2007-11-05
Hi Neill

I think I have the same tuner- a WinTVUSB2 My dmesg says:

Nov  4 12:54:26 athlon kernel: [   14.625736] tveeprom 1-0050: Hauppauge model 42012, rev C186, serial# 2817055

The driver for the WinTVUSB2 that is built into the Fiesty and Gutsy kernels never fully worked for me;
I am in Canada and I think the chipset is slightly different than Europe. I could not turn off the sound after I exited tvtime.

I had to  build the external module (ie what Microsoft would call the 'driver') for the Em28xx chipset, which is what all Hauppauge WinTVUSB2 use.

There is a Ubuntu wiki  article on how to do this. [https://wiki.ubuntu.com/em28xx]("https://wiki.ubuntu.com/em28xx")

I know Ubuntu is Linux, but maybe before attempting to build the em28xx module try shutting down your system, unplugging USBTV then reboot and plug in. I have found this fixed mine sometimes. I think something inside the USB2 does not reset properly after you change drivers and you need to power it and the kernel down for them to be happy again.

Good Luck

BTW did you have the same sound problem with yours with the kernel driver?

---

### Post by wayfarer51 on 2007-11-11
> **Jose Catre-Vandis said:**
> what is the chip onboard? (e.g. bttv/saa7134/cx88 )

I have no idea.  How would I find out?


> **dixonstalbert said:**
> 
BTW did you have the same sound problem with yours with the kernel driver?

Absolutely not!!  Everything in Tvtime worked after simply plugging in to a USB port in Feisty.  If I knew how to revert to Feisty without losing any of my setup and files, I would.  Is there such a way that's relatively easy to accomplish.  Other than getting Thunderbird 2, Gutsy is a step down from Feisty IMO.

Neill Dumont

---

### Post by Jose Catre-Vandis on 2007-11-12
Looks like its the Em28xx chipset :)

Follow dixonstalbert's link to try a drvier install from there :)

---

### Post by wayfarer51 on 2007-11-12
Life. Is. Good.

Went through the whole process; not as painful as I thought it might be.  I've got the picture on all my cable channels.  No sound yet...I've had to wrestle with that before and feel confident of victory.

Thanks to both of you.  Now to catch up on Heroes. :lolflag:

Neill Dumont

---

### Post by kblood on 2007-12-21
Hello,

I have a Gadmei UTV 330, and it also uses the em28xx driver.

I followed the guide to compile the em28xx module, and now the tuner works :popcorn:

However, I get no sound. Since you say you had to wrestle with it in the past, and that you were confident in victory, I have to ask... So, were you victorious?? :)

My card has a separate audio cable, so the sound should be coming in through the line-in input in my sound card, but no luck. I will be fighting with it a bit more this weekend, so any advice for preparation for the fight would be welcome :)

---

### Post by wayfarer51 on 2007-12-22
Hi,

I wish I could help, but the details of my glorious victory escape me.  :cool:   Honestly, I just can't remember.  Sorry.

Good luck.

Neill

---

