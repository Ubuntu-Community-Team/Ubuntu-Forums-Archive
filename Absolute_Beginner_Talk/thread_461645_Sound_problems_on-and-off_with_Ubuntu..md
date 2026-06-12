---
title: "Sound problems on-and-off with Ubuntu."
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Happybattles on 2007-06-01
When the sound works, it works great.  I log off and my daughter logs on and instantly it doesn't work.  She logs off and I log on and it works again.  Sometimes it comes back on it's own, sometimes I have to restart.

Didn't have any sound problems with Windows so I doubt the card went bad.  It's a SB Audigy LS.  Here's my basic info:

- - - - - - - - - - -

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

- - - - - - - - - - - -

Tried messing with the different mixers for an hour or so, not making any difference.  Now I can't get the sound back on no matter what I do.

I checked the Creative Labs website for a Linux driver and though they list the option, I can't find one.

---

### Post by ironfistchamp on 2007-06-02
This might be a stupid suggestion but it appears you have on-board sound aswell. Is it off in the BIOS? I once had this problem that only showed up in Linux but Windows was fine with it. 

If that isn't the issue I don't believe I can help. Sorry.

HTH

Ironfistchamp

---

### Post by blue_shift on 2007-06-02
I've got a discreet sound card and onboard sound, both enabled and I have no problems now. If you have two speaker jacks then you can quickly tell if the sound's jumped to outputting on the wrong card by switching your speakers over. There's a config file which allows you to choose output preference iirc.. anyone?

---

### Post by STREETURCHINE on 2007-06-02
you would not happen to have edgy 6.10 installed would you.

i have the same thing with edgy.
dapper is fine sound works all the time.
feisty is fine sound works all the time.
edgy is crap sound works every other boot if im lucky.

how could they have got the middle release wrong.

---

