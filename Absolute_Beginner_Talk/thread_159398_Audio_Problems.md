---
title: "Audio Problems"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by theycallmemorty on 2006-04-12
I'm currently having a ton of problems with my audio programs, starting from when I tried to install Enemy Territory.

WhenI go to the default music player I am able to play music, but when I try to play anything in Amorak I don't hear anything, however I know the song is playing because the bars at the bottom bounce along.

Any ideas?

---

### Post by therunnyman on 2006-04-12
I've got some!

You can either use the GUI (double click on the little speaker icon next to the time) or you can type "alsamixer" in a Terminal.  The latter is better, becuase you can see everything (I'm assuming here you're using ALSA - that'll be the default on your default device).

Whatever you choose, it's simply a matter of adjusting bars until sound comes out.  In the GUI, slide.  In alsamixer, use the arrow keys and "Q" "W" "E" for up, and "Z" "X" "C" for down.

Fiddling will set you free!  Unless you're Nero, then you'll go down in history as a jerk.

therunnyman

---

### Post by da5id on 2006-04-12
[QUOTE=theycallmemorty]I'm currently having a ton of problems with my audio programs, starting from when I tried to install Enemy Territory.

WhenI go to the default music player I am able to play music, but when I try to play anything in Amorak I don't hear anything, however I know the song is playing because the bars at the bottom bounce along.

Any ideas?[/QUOTE]

Longshot -- go to Aplications/Sound and Video/Volume Control -- look at your controls and see if they match your soundcard/chip and none of the important ones are muted -- eg, playback and it says ALSA mixer.

Good luck, the blind leading the blind.

--Gene, A.B.

---

### Post by theycallmemorty on 2006-04-12
Those didn't work.

My volume settings are correct apparently.

---

### Post by therunnyman on 2006-04-12
Hrm, soundcard...what do you have for a soundcard?  Tell me too (or better yet, shoot screens) of alsamixer (the terminal way).

therunnyman

---

### Post by nemequ on 2006-04-12
therunnyman was probably on the right track. Fire up gnome-volume-control and make sure nothing is muted (not just the sliders, the little mute/unmute buttons below them). If everything you see seems okay, go to Edit -> Preferences and start enabling sliders, then make sure everything is unmuted. I've seen that work four times (twice to me, once each to two of my friends)--dunno why Ubuntu wants to disable this stuff...

---

### Post by therunnyman on 2006-04-12
It looks nefarious, but ALSA and Ubuntu mess things up for your health, seriously.  Feedback is destroying the ears of the youth, and not in a good way, like Jimi Hendrix did.  When a microphone receives its own signal (like if you have a mic armed and your speakers armed), you get a nice dose of feedback.  Bust you eardrum up right good.

Folgers, good to the last drop,

therunnyman

---

### Post by theycallmemorty on 2006-04-12
Okay I went to the gnome audio control thing.

Under File -> Change Device I have two entries:

- Intel 82801BA-ICH2 (Alsa Mixer)
- Realtek ALC200/200P rev 0 (OSS Mixer)

I enabled all of the sliders for all both devices and ensured that all output sliders were turned up and unmuted.

I'm still not hearing anything when I play in amorak.

---

### Post by therunnyman on 2006-04-12
I assume the volume is at a proper setting in amaroK (I forget stuff like that all the time)...

The GUI doesn't show everything, exactly.

Don't fear the terminal, or the Reaper.  The terminal, located in Accessories--> Terminal.  Once that bad boy is fired up, type "alsamixer" (no quotes).  What's happening in there?

therunnyman

---

### Post by theycallmemorty on 2006-04-12
I dont fear the command line.  When I'm at school we use solaris and our machines are so crappy that the 'flashy' people use IceWM and EVERYONE does their work from the commandline.

Anyways, alsa mixer looks fine right now....

Volume in Amorak is at 50%, where it was when it was last working.

---

### Post by therunnyman on 2006-04-12
Oh man, I'm at a loss now...

Uh, lessee...fill me in on Enemy Territory.  Is it one of those newfangled deals where you speak with other players?  What's your hardware rig?  Surround speakers?  Dual?  Volume knob?

The other thing is, are you running amaroK on a GNOME desktop?  That's been known to cause problems.  It sounds like the fault is there.  If so, try a reinstall of amaroK after you've saved your lists and whatnot.

therunnyman

---

### Post by theycallmemorty on 2006-04-12
I'm pretty sure that Enemy Territory doesn't have anything that allows the user to talk to other users... I know the windows version doesn't.

My speakers are pretty generic... one plugs into my motherboard and the other plugs into that.  So there is only one knob.

I tried 'completely removing' and installing amorak... and when I did I got a message in the status bar saying the xine engine could not be found, using arts instead.

What engine does rythmbox use?

---

### Post by therunnyman on 2006-04-12
Excellent!  You found the problem.  Is everything working now?  Or do you want to use amaroK?  If so, you may want to switch to the KDE desktop (Kubuntu) to prevent further issues.  There probably is a way to nab xine for GNOME (right?  guys?), but I'm not sure what it is.  Checking the repositories would be my first step.

RhythmBox can use ALSA and OSS, it doesn't care.  And it's light.  That's why I hold it dear.

amaroK and the KDE desktop in general use more resources than GNOME.  If your machine is souped up, or can deal with bloat, I'd say go Kubuntu.

therunnyman

---

### Post by theycallmemorty on 2006-04-12
No the problem is that amorak isn't working and thats the one I want to use. :)

---

### Post by theycallmemorty on 2006-04-12
Oh and I should point out that sound works correctly when I use mozilla to look at a site with Flash like homestarrunner or something.

---

### Post by therunnyman on 2006-04-12
Okay, looks like there are several xine engines in Synaptic, or "apt-cache xine," if you're terminal.

Here's what I'd do: uninstall amaroK again, nab xine or some permutation of it, reinstall amaroK, et voila, or not.  There's the issue.

Experiment liberally, in all areas of life.

therunnyman

---

### Post by theycallmemorty on 2006-04-13
Here is the message Amorak greeted me with this morning:
> Sound server informational message:

Error while initializting the sound driver:

device: defaul can't be opened for playback (Device resource busy)

The sound server will continue, using the null output device.

---

