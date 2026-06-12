---
title: "Jack howto, ground zero starting point."
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Sou Portugues on 2007-10-08
So,

Not to be overly punny, but my system hasn´t got Jack. Actually it does, but I can´t quite seem to start or use it.

I fully assume this to be user error.  The problem is, I not sure I understand how this program works, more than conceptually, and loosely at that. It&#347; a virtual patchbay and master controler for audio, or programs using audio. I can patch one thing into another (or multiple things) and start (play, or record, or some combination of commands) all from the same program (the same button actually).

Is there a site, a pdf, a howto, or some other form of documentation archived away somewhere in the digital ether, that is a step by step howto (a users manual if you will), perhaps with some screenshots and explanations of buttons and options?

Perhaps something like this (but for jack)-
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)
or even this-
[http://ubuntuforums.org/showthread.php?t=171507](http://ubuntuforums.org/showthread.php?t=171507)

I going to work, so I apologize about the immediate lack of responses this will get from my end, but I will check this again in the morning (bout 10am Central), and most of the day tomorrow (10-9-07).

Feel free to post up what you have, and thanks in advance.

---

### Post by Sou Portugues on 2007-10-08
PS-
because I know someone will want to get specific to my problem (which isn really what I was going for here, but if you want to, feel free)....

This is what Jack tells me-

Could not connect to JACK server as client.
Please check the messages window for more info.

The messages window says this-

22:53:22.721 Patchbay deactivated.
22:53:22.756 Statistics reset.
22:53:22.782 MIDI connection graph change.
22:53:22.962 MIDI connection change.
22:53:28.038 Startup script...
22:53:28.038 artsshell -q terminate
22:53:28.274 Startup script terminated with exit status=256.
22:53:28.274 JACK is starting...
22:53:28.274 /usr/bin/jackd -dalsa -r44100 -p1024 -n5 -D -C/dev/dsp -P/dev/dsp -S -i1 -o1 -H -M
22:53:28.276 JACK was started with PID=23385 (0x5b59).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... /dev/dsp|/dev/dsp|1024|5|44100|1|1|hwmon|hwmeter|-|16bit
ALSA lib control.c:910:(snd_ctl_open_noupdate) Invalid CTL /dev/dsp
control open "/dev/dsp" (No such file or directory)
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
22:53:28.294 JACK was stopped successfully.
22:53:28.295 Post-shutdown script...
22:53:28.295 killall jackd
jackd: no process killed
22:53:28.503 Post-shutdown script terminated with exit status=256.
22:53:30.347 Could not connect to JACK server as client. Please check the messages window for more info.

Thanks again folks.

---

### Post by tgalati4 on 2007-10-09
A simple way to get into audio production is to burn yourself a copy of Dynebolic 2.4.2.  It's a live CD for music/artistic production with a real-time kernel.  There are some help guides at dynebolic.org.  

Basically, you need to setup Jack with the proper buffer size to minimize both xruns and latency.  Latency affects how long it takes to process sound before you hear it.  Normally you can sing to a few milliseconds, any more than that and it screws you up.  Xruns will cause digital glitches so you need to increase buffer size.  More buffer will increase latency, so you need to find a compromise.

Start the Jack server (jackd) from the control panel.  Make your patches between devices and software channels.  Run your Ardour or other jack-capable sound program.

¡&#596;&#305;sn&#623; &#477;&#623;os &#477;&#670;&#592;&#623;

---

### Post by Tom Mann on 2007-10-09
Don't forget UbuntuStudio, 64Studio and StudioToGo!

BTW, Upside down text? How?!?

---

### Post by Sou Portugues on 2007-10-09
Thanks Tom and tgalati4, I appreciate your replies.

Actually, I´m not looking for an OS, I´m looking to understand the OS I have.  I have used dyne, ubuntu, and studio64 before, in fact I just loaded ub-studio and rather like it.  But I still don´t understand the nuts and bolts of how JACK works.  My degree was in music production, so I am no stranger to studios, but I am a stranger to unix, as that was not what I studied.

Really, I am just looking for some sort of tutorial or guided introduction to JACK, without the technical jargon that often time goes along with linux howtos (not everyone reads code that well people).

Thanks

---

### Post by tgalati4 on 2007-10-09
I assume you have read through the Jack site:

[http://jackaudio.org/](http://jackaudio.org/)

And you have installed the Qt based control panel:

[http://qjackctl.sourceforge.net/](http://qjackctl.sourceforge.net/)

What specific questions do you have?

ps:  Flip text:  l&#623;&#647;&#613;&#729;d&#305;l&#607;\&#623;o&#596;&#729;p&#592;&#607;&#652;&#477;&#633;&#729;&#653;&#653;&#653;\\:d&#647;&#647;&#613;

Sorry:  [http://www.revfad.com/flip.html](http://www.revfad.com/flip.html)

---

