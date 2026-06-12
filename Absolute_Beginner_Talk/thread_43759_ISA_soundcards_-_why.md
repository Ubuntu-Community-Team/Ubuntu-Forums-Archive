---
title: "ISA soundcards - why?"
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by heltinde on 2005-06-23
Can anyone explaine to my, why it is so hard for Ubuntu to detect ISA soundcards? I've tried 3 different cards which are supported by ALSA, but were totally ignored (I did try all the suggestions from several fora).
I've now switched to a PCI card, but I would like to know, why Ubuntu hates ISA.

---

### Post by andlinux21 on 2005-06-23
not sure why it has a hard time setting up sound but otherwise everything else has worked for me.

---

### Post by heltinde on 2005-06-23
I've grown fond of Ubuntu - it's my first serious experiment with Linux. I figured it's normal to use the "old" pc for Linux until one gets used to it - and then switch 100% to Linux on the "new" pc. 
Therefor I think it's sad Ubuntu/linux doesn't detect at least the most common known ISA Soundcards.
In my opinion it's a bit to early to forget the support for ISA.

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=heltinde]
I've now switched to a PCI card, but I would like to know, why Ubuntu hates ISA.[/QUOTE]

It doesn't hate ISA. It doesn't like ISA. Its neutral. If I had to guess a reason why, its because soundcards of that generation:

1. may not be detected by hal

2. may be so old that linux drivers where never created

3. honestly, Ubuntu is quite a heavy OS resource wise, so the devs have made many decisions to focus on more modern hardware.

Oh course, these are all guesses. If you must know the real truth, you have to email a dev.

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=heltinde]
In my opinion it's a bit to early to forget the support for ISA.[/QUOTE]

I haven't seen a mobo sold with an ISA slot in YEARS!

---

### Post by heltinde on 2005-06-23
Yes, I know it's a couple of days ago ISA cards were sold ;-) The ones I tried were all supported by ALSA. The BIOS did detect all of the cards, but that was it.
The PC's I'm playing with currently are 5 - 6 years old, and they have the soundcard on the mobo. Because it didn't work, I got some free ISA cards since there is a single ISA slot on the board. I just wanted to try it out - no luck at all. - I'm having a hard time accepting that Windows can do something, that Ubuntu can't.
But it's funny to find the limits - I'm learning a lot in a short time.

Forgot to ask: What is hal?

---

### Post by Kvark on 2005-06-23
[QUOTE=heltinde]Forgot to ask: What is hal?[/QUOTE]

HAL is a device manager that keeps track of the hardware devices.

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=heltinde] - I'm having a hard time accepting that Windows can do something, that Ubuntu can't.[/QUOTE]

Try installing an EXE.

---

### Post by Kvark on 2005-06-23
[QUOTE=poofyhairguy]Try installing an EXE.[/QUOTE]

Ok, i tried, it worked just fine with wine.  :razz:

---

### Post by wvslkr on 2005-06-24
FWIW most isa cards will work.  Most 2.6 kernels are not compiled by default to detect them.  I do not know the reason for this, I suspect boot time probing for legacy hardware or problems with pnp reporting  routines.  

If however you know what your card is, it is generaly a quick google for the driver, then modprobe the driver to get it to work.  YMMV because some were a total pain to get working even when they were supposedly supported.

In short most will work, you just have to set them up yourself. :)

---

### Post by heltinde on 2005-06-24
I have tried setting up the different cards manually (made a file under /etc/modprobe.d and did modprobe afterwards). I found all the drivers in ALSA, but when modprobing I got the famous 'no such device'.

Poofyhairguy: What do you mean by EXE?

wvslkr: Eh what does FWIW and YMMV mean - I guess it's short hand for some common expressions....

---

### Post by wvslkr on 2005-06-25
Sorry for the shorthand.  For What It's Worth and Your Mileage May Vary. :)  

Just out of curiosity, what cards were you trying to set up?  Also, after rereading your posts, if I understood correctly, you have an onboard soundchip.  If this is the case if that chip is not disabled in bios it would interfere with the other cards setting up correctly.  The os will assume this is the default chip and not accept another driver because it is expecting one for the onboard chip.  If you want to fool around with this post and I will try to help.  Need some hardware specifics.

GL: Enjoy Linux ;-)

---

### Post by heltinde on 2005-06-25
Hello wvslkr (hard to remember)

I did remember to disable the onboard soundchip in BIOS (ESS 1869), before installing the others. Sometimes I got some sound out of the onboard chip, but it disappeared all the time. I tried Opti (know it's poorly) and a Yamaha (YMF719). Forgot the last one. Actually my best succes was with the es1869. I didn't even get a small beep from the others.
As I told earlier I have switched to a PCI card, because the computers I'm setting up needs to be easy to reinstall for people playing with Ubuntu for the first time (if they are just a bit like me, they will NEED to reinstall...). I want them to get an 'out-of-the-box' experience.
I have 3 identical Compaq Deskpro's, and they are working like a charm (600 mhz, 256 mb ram, the graphic card is with only 4 mb, but is expandable). I'm gonna use them to introduce people to Ubuntu.

---

