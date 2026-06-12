---
title: "Sound in left channel only...."
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by rondamato on 2007-11-29
Hey there,

I am not, despite the title of this room, an "absolute" beginner with Ubuntu, but damn close.

I have posetd before with this problem with no replys.  I have sound, but only left channel sound at the jack.  I tested the sound chip with a DOS boot and it works.  Ubuntu finds it, but only the left channel works!  Shows up in lspci, amixer shows its output as "mono" and alsamixer is all centered with nothing muted and external amplifiers off--all levels centered balance-wise.

Re-loaded and compiled the AC97 drivers, sound is BETTER but all left channel still!  Weird...  Forum searches show that this sound chipset shows problems in Ubuntu.

Here's the question--I don't expect anyone to "fix" this for me, but I have NO way to get into BIOS on this thing!  It's an HP Pavillion with an AMD 3100+.  It SAYS to just hit <F1> as usual (I've been a PC tech for 25+ years) but it does NOT "see" the <F1> with both a PS/2 and a USB kb.  FRUSTRATING!  Even disconnecting the HDD won't trigger a BIOS enter.  So...oh yeah the question...if I just plug in a PCI SB card and CANNOT shut off the OB sound thru BIOS will Ubuntu "see" the new card instead of the OB sound if they are both on 0220x-5-1-5?  Or will PnP just reassign the new card's resources somewhere else even though BIOS PnP (I think) is off?

What do you think?  Anyone have experience with these all-integrated HP platforms and Ubuntu?

ANY ideas will be greatly appreciated!!!

---

### Post by rondamato on 2007-12-15
Man oh man, this ran me thru the wringer.

25+ years of doing this and I have never failed at a computer-related task--ever.  I thought this would be the first.

After pouring over tons of discussion boards for all variants of Ubuntu, Debian, and all else I was about to give up.  I mean, pretty cut and dried...no right channel--plug headphones directly into the SPKOUT jack on the back of my PC (HP Pavilion w/integrated Realtek sound) and only a left channel appears.  Uninstalled and reinstalled all Linux sound support--nothing.  I learned to deal with it over the past few weeks but I hated using the Mac for anything that required stereo.  

Yesterday, I looked at the outside of my PC very closely while dusting it.  I never really noticed or cared that it has a 15-in-1 card reader in the front panel--plus two more USBs, FireWire, and 2 1/8" stereo jacks for mic in and sound out.  Hmmm, that's cool...  A thought occurs:  I plugged my 'phones into the FRONT audio out--same story, still no left channel.

I proceeded to open up the PC.  With a meter and and o'scope, I figured (boy is THIS a DUMB design!) that the inboard sound is fed OFF the motherboard by a 10-pin connector (actually 9-pin--one pin is absent for a "keyway") and up to the front panel's 1/8" jacks.  Since the "sound out" front jack on this machine is BROKEN (one stereo lead had TWO wires I further noticed--one TO and one FROM the sound chipset perhaps?) I started thinking...

I unplugged the sound cable from the MoBo.  NO sound then at either jack, so it MUST have to travel to the panel first before being backfed via the 9-conductor wire and output at the back.  The back sound-out jack is SOLDERED ONTO the MoBo also, so weird!!!!  I'm sure that there's a reason for this, but what it is escapes me.  I hate this HP SOO much.  If I didn't garbage-pick it with 2GB RAM, a 500GB, and a CoreDuo 1.8 AND an NVidia 8600(!) I would NOT own it.  Or anything else HP makes that doesn't a) use toner to print and b) isn't specifically made to fit into a 19" rack running HP-UX.

I jumped over the broken front jack with a bit of solder to "fake" a pair of ";phones" plugged into the jack.  I reconnected the cable to the MoBo.  Guess what??

Perfect left-right sound from the back jack!  I tested it via speaker-test--all channels are working independently of one another--no mono, no right-channel-only.

Soooo, the moral of this story is the same thing I learned from my mentor over 25 years ago--"if all else fails there's a HUGE probability that it's some cable's fault!"  So many times--especially in this age of USB, FireWire, Wi-Fi, and Bluetooth I find myself forgetting that admonition.

He was right.

Thank you all for the ideas to try--I learned SOO much from them at the very least!

DoctorRon

---

### Post by jeffemmert on 2008-04-13
Dr. Ron, I have a similar problem with left channel only on Ubuntu 7.10 (both channels work fine when I boot in XP Pro from the C: drive). It's an old GW 600ygr laptop with an ESS Allegro-1 sound card. The software tests properly recognize the hardware and the levels look the same on the graphs.

I was hoping for a simple connector problem but I think it's an o/s bug on mine.

Ideas?

---

