---
title: "No sound output"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by zumda on 2007-06-20
Hello everyone!

I just started with my little Linux experiment and got most of the things to work, but I still have no sound.

I have a bit a strange setup so I'll explain that first. I have actually two sound cards. One on-board (a C-Media CMI9880 according to the "Sound Preferences") and a Creativ Audigy 2 ZS.

Both are recognized somehow, because they show up in lspci

The two lspci  -v entries for the sound cards:
> 02:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs SB Audigy 2 ZS (SB0350)
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at a000 [size=64]
        Capabilities: [dc] Power Management version 2

02:01.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at a400 [size=8]
        Capabilities: [dc] Power Management version 2


> 00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Giga-byte Technology Unknown device a005
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f2000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0


I also played around with the this volume... thingy in the upper right of the gnome panel, but somehow I managed to remove it (or it removed itself, I'm not sure), but the sound didn't work befor, and it wasn't mouted, either.

So I have basically two questions:
1. How do I get some sound?
2. Just as a bonus. In windows I used (or still use, watching movies without sound is sooo boring... :D) one card for my 5.1 headset, and the other for some tiny speakers. Is there a possibility to change that easily in Linux (I know it's not the best setup, it's the only one I have... :D)

So I hope someone can help me here and thanks for you help!
zumda

---

### Post by Alex&amp;Linux on 2007-06-20
Heyo!

Use alsamixer!

Terminal:

 "alsamixer" without quotes

Check for green fill in indicators, use arrow keys to navigate!

---

### Post by zumda on 2007-06-20
I tried that, unmuted everything, but I still can't hear anything.

How do I know on which sound card I should have sound? Or does it stream it all ALSA-cards?

But then again, that shouldn't be the problem, since I have unmouted everything...

---

### Post by zumda on 2007-06-21
Has no one another idea?

---

### Post by number58 on 2007-06-22
im having the same problem

---

### Post by paradoc on 2007-06-22
As a stop-gap, and until you get your NOSOUND problems sorted, you might like to try using USB speakers. This might explain why:

With System>preferences>sound>USB Audio...the 'test' is ok--- leave settings as, and Close.
Ubuntu Sax.ogg (in examples), now plays from both Feisty  and (if setup the same) on liveCD in Feisty
If left on Autodetect though,(in sound preferences), the USB speakers will be silent when the main speakers are turned off.

All of which now seem to be quite a normal response if setup is as above.
[U]The self-powered USB speakers are independent of sound cards, as they have their own built-in sound.
[/U]
It was a little confusing at first to me, I hope this helps someone with the same problem.;)

---

### Post by gcos7 on 2007-06-22
Okay, I'm no expert in this, but I can tell you something that seems counter-intuitive but worked to get the sound working on my Gateway laptop using the alsa sound manager.  Via edit and preferences, I have to have external amplifier enabled, then on the general screen I have to go to switches and uncheck external amplifier.  I know this makes no sense, but it works for my setup.  Maybe it might work with yours?

---

### Post by zumda on 2007-07-03
Just in case someone stumbles over this post, I know now what the problem was. Somehow the default device was a third device without real audio playback. So I just set the alsa-defaults in /etc/asound.conf and it worked (after I unmuted everything. And I didn't try the mic yet.)

See more about how to set the default here: [http://alsa.opensrc.org/index.php/FAQ026]("http://alsa.opensrc.org/index.php/FAQ026")

---

