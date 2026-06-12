---
title: "Headphones and microphones won't work, HELP!"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Tangerina on 2007-09-27
Hi, so, I always loved the idea of Linux and open source, etc... so I got my boyfriend to set me up with Ubuntu... and then he became my ex boyfriend and I left to study abroad in Greece with no computer nerds until December. I'm ok at computer stuff, but the second it gets truly technical I'm in way over my head. My computer speakers work fine, but so far I can't get any sound out of headphones and I tried a USB mic and that didn't work either. The computer recognized that a mic was attached, but didn't pick up the sound. I tried messing with all of the volume settings, and it didn't help one bit. I tried downloading the alsa mixer, because the mic showed up with the word alsa so I started looking into that, but the mixer doesn't load and when I go into my normal mixer it says ogg. The last 2 sentences probably show how not savy I am about Linux and computery stuff. When I plug in the headphones, the computer speakers turn off, but no sound comes out of the headphones. Headphones are kind of important since I'm living in a 1 bedroom apartment with a room mate until December, and the microphone would let me use Skype to call home. Does anyone have any suggestions they can walk me through? I'm willing to learn but it might take some patience. Please help!

---

### Post by gautada on 2007-09-27
> **Tangerina said:**
>  I tried messing with all of the volume settings, and it didn't help one bit. 

You said you did this already but since this is a process lets start here:

Right Click: Volume Control Applet->Open Volume Control
Set all channels to 100%
Plug-in you headphones and microphone (make sure this is correct)
Headphone Test: Click System->Preferences->Sound: Click "Sound Playback" "Test" button
Microphone Test: Click Applications->Sound Recorder: Try to record some sound

If that fails then:
Click: System->Preferences->Sound: See if you have multiple mixers select another mixer and try again.

---

### Post by Tangerina on 2007-09-29
Thanks for the reply, I tried all that and it didn't help. I got it to work once I learned to get to the alsamixer through the terminal (YAY!) but then someone pressed some buttons on the computer and the sound problems got 50X worse and now it won't let me get to the alsamixer through the terminal, it says Invalid Argument. I'm going to write a separate post about it.

---

