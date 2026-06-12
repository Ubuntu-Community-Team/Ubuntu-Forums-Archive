---
title: "getting my USB MIDI interface working (Edirol UM-2)"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by duncancan on 2007-08-01
Hi everybody,

I don't even know where to start with this one, sorry. What is it in Linux that handles MIDI? ALSA? JACK? i've found [this]("http://homepage3.nifty.com/StudioBreeze/software/usbmidi-e.html"), but it seems a little antiquated.

the UM-2 is a generic USB-MIDI interface -- how do i get it working and talking to things like rosegarden?

thanks,
-duncan

---

### Post by Mark_in_Hollywood on 2007-08-02
1st -- sorry I don't have answers

2nd -- alsa is the "driver" for sound cards. If the sound card can be made to work at all with alsa, and some cannot, then if you get a sound Timidity++ can play midi back. I'm referring to pci internal pc cards that fit into the computer. USB? Never heard of a usb sound card.

If you are trying to compose, and I think you are, you should contact the makers of the midi software and hardware. They will know what works.

Try reading:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I issued this caveat: be careful. I did this with outdated info and had to do a reinstall.

A moment later after posting this, I looked at this Edirol UM-2. I see MAC listed, but not Linux. You should have googled: Edirol UM-2 and HCL (hardware compatibility list) to see if anybody else got it to work. 

See these:

[http://alsa.opensrc.org/index.php/MultipleUSBAudioDevices](http://alsa.opensrc.org/index.php/MultipleUSBAudioDevices)

[http://www.qbik.ch/usb/devices/showdev.php?id=1244](http://www.qbik.ch/usb/devices/showdev.php?id=1244)

---

