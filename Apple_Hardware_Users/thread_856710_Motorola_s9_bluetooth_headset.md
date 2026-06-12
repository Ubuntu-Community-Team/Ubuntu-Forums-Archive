---
title: "Motorola s9 bluetooth headset"
date: 2008-07-11
forum: Apple Hardware Users
---

### Post by senuxis on 2008-07-11
I've been trying to set this up with ubuntu but I've had no joy. An error about OBEX keeps popping up. Please help.
This is the error that I get:

Couldn't display "obex://[20:08:04:25:08:3F]/".
Error: Host down
Please select another viewer and try again.

---

### Post by deb on 2008-07-13
I have the exact same problem as Senuxis with my Macbook pro SR (sept 2007).

Motorola S9 is an A2DP device and I have bluetooth-alsa package installed in Hardy with latest updates.

I will not say I have exhaustively searched the net but my initial effort is not giving me any clue. 

If any of you made some headway with any A2DP device and Macbook pro, will be very interested to know.

thanks in advance.
Deb

Further I tried to connect the device using Apple Tiger (10.4) and it did not connect... they say you have to have leopard for that!!! $125 just to connect your bluetooth headset???

---

### Post by deb on 2008-07-13
Ok senuxis, I have figured it out
go to this page [http://wiki.bluez.org/wiki/HOWTO/AudioDevices#audacious](http://wiki.bluez.org/wiki/HOWTO/AudioDevices#audacious)
1. make the .asoundrc file in your home dir.
2. configure your player amarok, xine etc to use alsa as audio driver and change the stereo output device to "bluetooth" (without the inverted commas).
3. pair the S9 and ignore the error message (I think the error comes because the laptop is trying to browse the headphone... but may be wrong). after pairing you should be having the red light on the S9 slowly blinking.
4. watch a movie or play some music, the sound should come through the s9.

---

### Post by hearthand on 2009-05-12
That fix won't work...
The error message is a obex communication error...The bluetooth adapter can see the headset but can not talk to it for some reason...

---

