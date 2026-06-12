---
title: "TVtime can't change channel and no sound"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by camini on 2007-02-06
Hello,

I've been reading almost all posts on tvTime and sound issues, but no rescue yet.
I've change the tvtime default from /dev/video0 to /dev/video1 to get a TV channel successfully.

Open issues:
-I can see 1 channel (the last one tuned in Windows XP) and have no sound.

-Scanning for channels does not help as the same channel keeps coming up.
- No possibility to change volume (only 99% and 100%)

What's wrong here?
I've got a bt878 TV tuner chipset.

dmesg gives the following:

pmvdv@pmvdv-desktop:~$ dmesg | grep bt
[17179587.648000] bttv: driver version 0.9.16 loaded
[17179587.648000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179587.728000] bttv: Bt8xx card found (0).
[17179587.728000] bttv0: Bt878 (rev 17) at 0000:01:00.0, irq: 74, latency: 64, mmio: 0xdfffe000
[17179587.728000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[17179587.728000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[17179587.728000] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[17179587.728000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[17179587.820000] bttv0: Hauppauge eeprom indicates model#44804
[17179587.820000] bttv0: using tuner=4
[17179587.820000] bttv0: i2c: checking for MSP34xx @ 0x80... <5>sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179587.824000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179587.824000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179587.864000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179587.916000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179587.956000] bttv0: registered device video1
[17179587.956000] bttv0: registered device vbi0
[17179587.956000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179588.152000] bt878: AUDIO driver version 0.0.0 loaded

---

### Post by fenian on 2007-02-06
See section 5 on this page

[http://tvtime.sourceforge.net/usage.html#channels](http://tvtime.sourceforge.net/usage.html#channels)

Although it has been quite some time since I used TVTime I remember having to write up an XML channel list by hand.

---

### Post by camini on 2007-02-06
Ok - that would be for the one-channel problem I guess?  What to do in Europe (Brussels)? Use VHF E series of channels?

Anyone with ideas for the volume and sound issue?  The tuner's output is connected to my SB audigy 4 - sound and music works - not yet in 5.1 - need to check that out as well..

Tx for the suggestions

---

### Post by Drakkor on 2007-02-06
Just a shot here, if you're in Europe, did you set it up for PAL ?

---

### Post by fenian on 2007-02-06
Download XMLTV its in Synaptic.Then follow these instructions for using XMLTV with TVTime.

[http://tvtime.sourceforge.net/xmltv.html](http://tvtime.sourceforge.net/xmltv.html)

---

### Post by fenian on 2007-02-06
As for the sound issue open the volume control panel (left click volume icon in panel and select open volume control) and make sure line in isn't muted out.

---

### Post by camini on 2007-02-07
Thanks! The volume control did the trick - I now have sound.  It was this little 'microphone' icon that was muted (capture toggle) - weird to have a microphone icon for this functionality..

I also have all my TV frequencies handy - so now I must try to enter these in stationlist.xml.
I will check out the XML TV first.

We're getting closer to a fully functional media setup :) 
Cheers

---

