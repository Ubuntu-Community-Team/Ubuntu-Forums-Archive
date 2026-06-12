---
title: "No sound in Audacity (and RoseGarden)"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by paker on 2007-05-25
When I click on Play Button, I get an error message.

(I took screen shot but don't know how to link to it) What it says is "Error while opening sound device. Please check the output device settings and the project sample rate."

I have an AMD 64 x2 motherboard with built-in sound. I have no sound problem playing mp3 and  wav files. I cannot play midi directly. I have to convert to wav first. Thanks for your help.

---

### Post by owise1 on 2007-05-25
Rosegarden needs a MIDI device to play its output.  If your sound card does not have a midi device in it and I am sure it wont then install Timidity.  From a terminal run "timidity -iA" .  Also have a look at "timidity -h" for other switches.  This will provide software emulation of a midi device.  You will need some grunt from your PC and for Rosegarden a real time kearnel.  Fro playing around I have had good results from a 1GHz PC with 512M ram.

If you have a keyboard (music) with USB midi support then once you plug it in you should be away!  You can record from and play to the keyboard - lots of fun.

---

### Post by FSHero on 2007-05-28
Thanks owise1 for the advice; in Knoppix 4.0, I remember that Timidity allowed me to play MIDI files.

Does that mean in Windows, when you play a MIDI file, it is coming through a software synthesiser?

Also, you said that, to use a software synthesiser, you need a fairly powerful PC. But I remember that I had an old AMD K6 that could play MIDI files in Windows 98, and everything sounded okay. What's that deal with that?

Finally, I have a Yamaha OPL3-SA2 (I think) soundcard. Does that have a hardware synthesiser? In Windows 98, I remember that in the MIDI devices list, I could choose FM synthesis. If my physics/computing is correct, FM synthesis is where waves are "superimposed" to attempt to make sounds like musical instruments (which often are not realistic!), and this sounds like it could be done by a hardware synthesiser. (For the record, I use Ubuntu Feisty now :D)

Sorry for the essay; thanks in advance!

---

### Post by owise1 on 2007-06-01
> **FSHero said:**
> Thanks owise1 for the advice; in Knoppix 4.0, I remember that Timidity allowed me to play MIDI files.

Does that mean in Windows, when you play a MIDI file, it is coming through a software synthesiser?

Same issue - soundcard dependent 

> **FSHero said:**
> Also, you said that, to use a software synthesiser, you need a fairly powerful PC. But I remember that I had an old AMD K6 that could play MIDI files in Windows 98, and everything sounded okay. What's that deal with that?

The power needs are more with Rosegardens requirements - really you should be running a realtime kernel - Try out Studio to go to see the difference

> **FSHero said:**
> Finally, I have a Yamaha OPL3-SA2 (I think) soundcard. Does that have a hardware synthesiser?

Lots on stuff on that card if you Google it.  If is had a MIDI capability then Rosegarden should have seen it.  You could check to see if you have a /dev/midi.

Cheers

---

### Post by FSHero on 2007-06-03
Good news (for me :) - I got Rosegarden working. I had to do a little fiddling though...

Before I even installed Rosegarden, I was once browsing through System Settings, and stumbled upon the Sound System --> Hardware page. Being a smart-alec, I changed the MIDI device from the default to "OPL3 FM synth  OPL3 FM Port - ALSA device". See the attached screenshot:
[ATTACH]34234[/ATTACH]

Anyway, today I installed Rosegarden, and imported a .mid file. I saw all the tracks 'fill up' (sorry about the poor vocabulary). However, when I clicked "play", no sound was heard. (The transport was counting the time played, however.)

I tried some more fiddling, by going to (menu:) Composition --> Studio -- Manage MIDI devices. The next attached screenshot shows the settings before I changed anything:
[ATTACH]34235[/ATTACH]

Under "Play devices", I changed the "General MIDI Device" setting from "17:0 OPL3 FM Port (write)" to "16:0 Yamaha OPL3-SA23 MIDI (duplex)". I closed the window, hit Play on the transport, and it worked!

Ahh, sweet music!

As people can probably tell, I'm quite a newbie; I'll have to read up on kernels, my sound card and the timer resolution error I keep seeing whenever I start Rosegarden.

---

