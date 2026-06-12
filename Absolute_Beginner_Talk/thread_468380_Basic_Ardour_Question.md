---
title: "Basic Ardour Question"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by niglch on 2007-06-08
I've downloaded Ardour-GTK from the Ubuntu repository, but when I try and run it, I receive a message saying that it cannot connect to JACK. I'm quite a noob to the multimedia programs for Linux and I have a very vague idea of what JACK is and what it does. Could anyone help me to fix this problem and get Ardour to start? I'm hoping to use it as a good mixer/editor for MIDI and audio files. I'm running Ubuntu Feisty.
By the way, what would the advantages be of using Ubuntu Studio over a regular distro?

Thanks

---

### Post by Thomaseov on 2007-06-08
same problem, same situation...someone, anyone.  As far as I can tell jack is indeed installed...

---

### Post by Thomaseov on 2007-06-08
niglch,

Figured out how to start it...at least on my setup in the main ubuntu program menu go to sound and video and launch "JACK control".  Hit the start button and then relaunch ardour.  Good luck.
Thomas

---

### Post by shen-an-doah on 2007-06-08
Yep, you pretty much just launch "Jack Control" and then hit the start button. Then launch Ardour. Ardour's great for audio mixing, but it doesn't really do MIDI. Try Rosegarden if you want MIDI and audio.

As for a reason to use Studio over regular Ubuntu; Studio comes with a low latency kernel by default. This means it takes less time for the audio signal to be converted to digital samples, which means you have less chance of there being glitches in the recording.

If you've got Feisty already installed and don't want to lose al your settings, etc by doing a fresh install of Studio, you can just add the repositories and install the studio bits. Click the link in my sig for instructions.

---

### Post by dannystaple on 2007-06-08
> **shen-an-doah said:**
> Yep, you pretty much just launch "Jack Control" and then hit the start button. 
Hmm - I have been using Jack with other apps for some time, but I do not have such a menu item. I am still starting jackd from the command line. Is there some package I am missing here for that?

---

### Post by shen-an-doah on 2007-06-08
> **dannystaple said:**
> Hmm - I have been using Jack with other apps for some time, but I do not have such a menu item. I am still starting jackd from the command line. Is there some package I am missing here for that?

The pakage is "qjackctl", as far as I know...

---

### Post by niglch on 2007-06-08
Agh, I installed Jack Control but I get an error message whenever I try to hit the start button:
```
21:48:03.035 Patchbay deactivated.
21:48:03.202 Statistics reset.
21:48:03.775 MIDI connection graph change.
21:48:03.779 MIDI connection change.
21:48:26.546 Startup script...
21:48:26.547 artsshell -q terminate
21:48:26.841 Startup script terminated with exit status=256.
21:48:26.842 JACK is starting...
21:48:26.842 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
21:48:26.850 JACK was started with PID=14807 (0x39d7).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
21:48:26.904 JACK was stopped successfully.
21:48:26.905 Post-shutdown script...
21:48:26.905 killall jackd
jackd: no process killed
21:48:27.131 Post-shutdown script terminated with exit status=256.
21:48:29.019 Could not connect to JACK server as client. Please check the messages window for more info.
```

I don't even think Jack will be that useful for me anyway however. Isn't it just for people who are recording MIDI or audio through instruments directly wired to their computer? In that case, it's not what I'm aiming to do. I'm thinking Rosegarden might be better because it's the only usable MIDI sequencer that I've seen so far even though I still haven't figured out how to add audio samples into it. Plus, it's slow in GTK, but I guess I'll deal with it. I would like to see Ardour running though...

---

### Post by shen-an-doah on 2007-06-08
> **niglch said:**
> Agh, I installed Jack Control but I get an error message whenever I try to hit the start button:
```
21:48:03.035 Patchbay deactivated.
21:48:03.202 Statistics reset.
21:48:03.775 MIDI connection graph change.
21:48:03.779 MIDI connection change.
21:48:26.546 Startup script...
21:48:26.547 artsshell -q terminate
21:48:26.841 Startup script terminated with exit status=256.
21:48:26.842 JACK is starting...
21:48:26.842 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2
21:48:26.850 JACK was started with PID=14807 (0x39d7).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
21:48:26.904 JACK was stopped successfully.
21:48:26.905 Post-shutdown script...
21:48:26.905 killall jackd
jackd: no process killed
21:48:27.131 Post-shutdown script terminated with exit status=256.
21:48:29.019 Could not connect to JACK server as client. Please check the messages window for more info.
```

I don't even think Jack will be that useful for me anyway however. Isn't it just for people who are recording MIDI or audio through instruments directly wired to their computer? In that case, it's not what I'm aiming to do. I'm thinking Rosegarden might be better because it's the only usable MIDI sequencer that I've seen so far even though I still haven't figured out how to add audio samples into it. Plus, it's slow in GTK, but I guess I'll deal with it. I would like to see Ardour running though...

Have you got anything else soundwise currently running? Even just an audio player that's stopped/paused.

Jack is useful for other stuff too, as it allows you to connect various audio apps together, meaning you can do a lot more with multiple apps rather than trying to do everything with one.

I'm pretty sure Rosegarden uses Jack too. If you want a dead simple MIDI sequencer, try Seq24.

---

### Post by bmcage on 2007-06-09
> the playback device "hw:0" is already in use. Please stop the application using it and run JACK again

Eg, Skype could be running

---

