---
title: "Audio Issues"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by jleemc44 on 2006-11-26
I have no audio from my system and I even checked to see that the speakers are connected, powered and turned up!:rolleyes: 

There are no errors when playing audio and the little volume control in the top right looks normal (no red slash). It even lets me change the volume. In the device list I see my audio device (82801G (ICH7 Family) High Definition).

The only thing I can think.....I've always used my analog speakers in windows and without problems. However, I know theres a fiber link, could it be that Linux caught on to this and is sending audio out this port? I did try changing the sound playback option in system > preferences > sound. It was set to HDA. I also tried the ALSA, ESD and OSS options.

Any ideas would be helpful.

Thanks Team!

---

### Post by Cardmaster91 on 2006-11-26
what o u not get audio in? first you should check the audio preferences of that specific program. and if its a windows program u r running with wine, be aware it might not be fully supported

---

### Post by jleemc44 on 2006-11-27
I'm not getting audio from any application. This includes system sounds and the system sound checker. I don't use wine or any windows software on my ubuntu distro.

---

### Post by xpod on 2006-11-27
Right click your volume icon and check your "volume control"

Or you can type "alsamixer" in the terminal and that too will bring you up some sound controls

---

### Post by jleemc44 on 2006-11-27
This too, I have tried. The mixer comes up and allows me to change all controls with no error message. Only problem, no sound comes out. This machine is dual booted with windows xp. I load windows xp and sound, so I know its not something stupid like the connection between the pc and speakers.

---

### Post by jleemc44 on 2006-11-27
Any ideas here? I could use a little help. Should I post any logs?

---

### Post by jerrybee on 2006-12-05
I wish I had some suggestions, but I'm working through something similar and am trying to figure out how to compose a description of the problem so that I can submit it to the forums.  But for what it's worth:  the sound works fine in Win2000 and Linspire, but not in Ubuntu or Fedora Core 6.  I thought I had no Ubuntu sound, but what I finally found was that when I tried to play a CD or a .wav file from the HDD, the playback time was moving horribly slowly -- e.g. it would take 5 minutes (don't laugh, I timed it) for the playback time to increase 1 second !!!  Some times it takes maybe 25 seconds to increase 1 second.  When I boot, the Ubuntu "tone" (I have no idea what it really sounds like because I've never heard it play normally)  starts a throbbing or pulsing monotone, at about 4 throbs per second, continues for a minute or 2, then the tone (note?) changes slightly and goes on for a while, etc etc forever.  Also, when I click on an icon or menu selection it takes maybe 10 seconds for the new window (or whatever) to display.
    The mobo is a MachSpeed with integrated VIA8235 audio.
    As a newbie, I have no clue what the cause or fix might be.  When I find it, I'll come back here and let you know.
              Jerry

---

