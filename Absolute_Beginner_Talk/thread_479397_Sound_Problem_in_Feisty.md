---
title: "Sound Problem in Feisty"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by gazzadtfan on 2007-06-20
Hi
I'm having sound problems at the moment and I'm unsure where to turn to. Having read some other posts I tried the following command in the terminal : lspci -v

It came up with the following:

02:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
        Subsystem: Creative Labs CT4780 SBLive! Value
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at ece0 [size=32]
        Capabilities: <access denied>

Not that it means a lot to me, being a beginner, but the last entry 'access denied' certainly raised an eyebrow or two, but I'm not sure what it means or how to try and sort it. Can anyone please advise me what I can do or direct me in the right direction?

Many thanks

gazzadtfan

---

### Post by yagood on 2007-06-20
Try this:

```
sudo lspci -v
```

---

### Post by gazzadtfan on 2007-06-21
Thanks yagood

after doing as you suggested I get the following display:

02:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at ecd8 [size=8]
        Capabilities: [dc] Power Management version 1

Given the above can anyone suggest a way forward to sorting my lack of sound. I am dual booting with XP and I get sound no bother with windows. I did get sound as well with Feisty but I'm sure the problems started after an update. I have tried loading Feisty with a previous version of the kernel but it is still the same.

Any ideas anyone?

gazzadtfan

---

### Post by yagood on 2007-06-21
When you go to System > Preferences > Sound and click some of the "Test" buttons, do you hear anything?

---

### Post by gazzadtfan on 2007-06-22
I don't hear anything when I do as you suggest. When I click on test it shows the 'Testing Pipeline' window and only 2 of the 10 blocks are highlighted on the bar. 

How long should I wait before I should hear anything? Should it be instant?

They are all marked as 'autodetect' with the exception of 'Sound Capture' which shows ALSA.

The Default Mixer Device shows my card.

thanks for your help yagood. It's much appreciated.

---

### Post by sunshine12 on 2007-06-22
If you are getting sound sometime and not at sometime, then your soundcard is not set at default..

If this is the problem then try this..

$ sudo asoundconf list

this will list the soundcard present on your device..
then

$ sudo asoundconf set-default-card ENTER-NAME-OF-THE-CARD

replace "ENTER-NAME-OF-THE-CARD" with your soundcard name as listed in above list..

Hope this helps..

---

### Post by orb9220 on 2007-06-22
[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound)

---

