---
title: "Stumped on Dial Up Connection"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by BrianV on 2007-04-28
I am new to Linux and Ubuntu. Have installed 6.10 on a Pentium III 500 MHz CPU with SoundBlaster 64AWE, a Cannon iP2000 printer, and an external US Robotics Sportster 33.6 modem connected via the serial port. None of these worked initially, but with the official book and user forum info I have the sound card working and the printer partially working.

I am stumped on the modem. It doesn't seem to be recognized by the system and I can find no useful information. This is the second modem I tried. The first was an internal ISA bus modem that also wasn't recognized, so I switched to the external one because the published info indicates external modems are easier!

Any diagnostic help or explanation of how modems are treated in Ubuntu will be great.

---

### Post by rengade_doode on 2007-04-28
Hi Brian:
Not sure if this is going to help. I am new to Ubuntu too.
However when I started using Ubuntu about 8 months ago  I had a dial up and had the usual problems of connecting to the internet. Then I got an ACTIONTEC external modem with serial port. set it to /dev/ttyS0 and everything was fine.

---

### Post by Chilli Bob on 2007-04-28
OK, have you tried this.  Go to this [[COLOR="RoyalBlue"]LINK.[/COLOR]]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9")

My advice is to try Alternative Way number 1.  It worked quite easily for me. (Make sure you modem is turned on before you start).  The onloy problem is that each time you want to use the internet, you have to open the terminal and run wvdial, but it's not a big hassle.

Hope this works for you.

---

### Post by BrianV on 2007-04-28
> **Chilli Bob said:**
> OK, have you tried this.  Go to this [[COLOR="RoyalBlue"]LINK.[/COLOR]]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9")

My advice is to try Alternative Way number 1.  It worked quite easily for me. (Make sure you modem is turned on before you start).  The onloy problem is that each time you want to use the internet, you have to open the terminal and run wvdial, but it's not a big hassle.

Hope this works for you.

Thanks, Chilli Bob,

I have already tried Alternative Way 1. The response indicates ttyS0 and 1 have been checked and that no modem was detected. It then asks, "Did you configure it properly with setserial?" Since I haven't a clue what this means I'm still stumped.

Also, since I'm trying to understand something about how Linux/Ubuntu works, just stabbing at anything until something clicks is not very satisfying.

---

### Post by BrianV on 2007-04-28
> **rengade_doode said:**
> Hi Brian:
Not sure if this is going to help. I am new to Ubuntu too.
However when I started using Ubuntu about 8 months ago  I had a dial up and had the usual problems of connecting to the internet. Then I got an ACTIONTEC external modem with serial port. set it to /dev/ttyS0 and everything was fine.

Thanks, rengade doode,

If all else fails I'll try switching modems as you suggest, but I'd really like to understand what is going on before doing that. Do you know anything that describes what is actually happening behind the scenes?

---

### Post by jitsu on 2007-04-30
I'm a novice also and have problems with dialup. Everything works in Ubuntu version 6.06 and doesn't in 6.10

I have an external modem, which is supposed to work and doesn't. I checked the mfg's website and they do have a linux driver for my model modem. 

By necessity, I have been reading and found that some Winmodems, internal card modems, can be made to work with a linux driver. 

Try Linmodems website at [http://www.linmodems.org](http://www.linmodems.org) and you may find some info there also.

good luck

---

