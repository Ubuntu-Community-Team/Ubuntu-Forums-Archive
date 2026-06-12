---
title: "failing jack's alsa driver on iBook G4"
date: 2007-07-18
forum: Apple PPC Users
---

### Post by nodonnel on 2007-07-18
Hi,

I just did a clean install of Fiesty on my iBook G4. The only packages I installed were upgrades and the ubuntustudio packages for audio, audioplugins, video, and graphics. I am an electronic musician, so first thing I launched Jack Control and pressed 'Start.' Jack Control stopped immediately and gave me this error log:

Sorry. The audio interface "hw:0" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
18:06:31.620 JACK was stopped successfully.

According to ubuntu, the device at hw:0 is a 'PowerMac Snapper.' I have come to this safe haven after googling to no avail. Seeing as I have a performance next week, any help you can give me would be close to saintly. Thanks a lot,

Nate

---

### Post by nodonnel on 2007-07-18
oh yeah, and before anyone asks I'd like to add that there is sound coming out my comp through Ubuntu, from the sound administration utility and also from the ZynAddSubFX synthesizer (just nothing that depends on Jack). Thanks

Nate

---

### Post by stmiller on 2007-07-18
Hey in qjackctl, try these options:

Driver: alsa

Soft Mode
Force 16bit
Frames/Period 64

See if that works.

You may want to compile a low-latency kernel to use realtime audio capabilities. Otherwise there will be timing problems with Rosegarden. Check out the PowerPCFAQs for a quick and dirty how-to.

---

### Post by mir123 on 2007-07-23
I'm having the same problem with an eMac G4 and Feisty, it works with oss but not with ALSA... already recompiled kernel for low latency ([http://ubuntuforums.org/showthread.php?t=453497](http://ubuntuforums.org/showthread.php?t=453497)) and tried the options above, but still can't start jack.

---

### Post by stmiller on 2007-07-23
What is the output in a terminal if you just do:

$ jackd -d alsa

---

### Post by mir123 on 2007-07-23
Hi stmiller!  Here it is:

$ jackd -d alsa
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
Sorry. The audio interface "hw:0" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns

---

### Post by mir123 on 2007-07-23
And here's the output with different options:

$ jackd -dalsa -dhw:0 -r44100 -p64 -n2 -s -S
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|64|2|44100|0|0|nomon|swmeter|soft-mode|16bit
control device hw:0
configuring for 44100Hz, period = 64 frames, buffer = 2 periods
Sorry. The audio interface "hw:0" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns

---

### Post by stmiller on 2007-07-23
Okay one more, try this:

```
jackd -R -dalsa -dhw:0 -r44100 -p64 -n2 -s -S
```

Sorry I don't have an iBook G4 to test at the moment.

---

### Post by mir123 on 2007-07-23
If I run it as normal suer...

$ jackd -R -dalsa -dhw:0 -r44100 -p64 -n2 -s -S
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 805439808, from thread 805439808] (1: Operation not permitted)
cannot create engine

$ sudo jackd -R -dalsa -dhw:0 -r44100 -p64 -n2 -s -S
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|64|2|44100|0|0|nomon|swmeter|soft-mode|16bit
control device hw:0
configuring for 44100Hz, period = 64 frames, buffer = 2 periods
Sorry. The audio interface "hw:0" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
ALSA: cannot configure capture channel
cannot load driver module alsa
Fallo de segmentación

(that last line means segmentation fault)

---

### Post by stmiller on 2007-07-23
Hm- I'm out of ideas.  :(

---

### Post by 2g3 on 2007-07-29
on DebianPPC(stable&unstable) and UbuntuPPC7.04
i could make sound with
chuck something.ck
by having
jackd -R -doss -r48000 -p1024 -n2
i began to wonder that
maybe we snapper people are just using fake ALSA
does this mean that we cannot take advantage of what
JACK exists in this Linux world for?

i compiles 3 versions of chuck on slackintosh
JACK version didn't bring out sound in the way written above
ALSA version doesn't work
OSS version gives a segmentation error

---

### Post by stmiller on 2007-07-29
Jack did work for me with an iBookG4 and Ubuntu in the past. I have since sold that computer, unfortunately. But I remember doing work with Rosegarden and so forth using soft synths with Jack. 

You can always upgrade to a newer alsa (or just compile newest kernel), along with latest jack to see if that fixes anything.

---

### Post by myo on 2007-09-30
hey, I'm gonna bump this thread because I'm having the same problem.

seems that on Ubuntu Feisty and Debian Lenny PPC the alsa drivers dun work with jack for the "snapper" soundcards. = \    I've had to start jack with -doss, which works, but I still get A/D/A sync issues. anyone have a solution yet? I've been working on this the past couple days so I'll post here if I find something.

---

