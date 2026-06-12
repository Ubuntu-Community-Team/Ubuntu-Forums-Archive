---
title: "Music play slowly"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by hillocom on 2007-02-13
hi. i am new to linux and ubuntu
on my ubuntu6.10, music files (mp3, wav) are played slowly and their pitch is low by about 1 tone.
i tried  aplay,  xmms,  bmp.  but all apps were same.
anyone meet this kind of problem?  I really want to solve.

forgive me for my poor english

---

### Post by tedrogers on 2007-02-14
This sounds like a sample rate issue to me.

I'm not sure how to fix this, but it could be that your sound card sample rate is not going to 44.1kHz or your sound files are playing back at 48kHz.

Post some more details about your sound chip type, desktop / laptop type, other hardware etc.

Also, you might want to install Audacity and try a sound file with that.

You can get this simply by googling for Automatix, get that and install it, then from within Automatix load all of the relevant audio codecs and Audacity as well.

Or use this link:

[http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.14-6.10edgy_i386.deb](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.14-6.10edgy_i386.deb)

Within Audactiy make sure the sample rate is set to 44100 / 44.1 kHz and load a file in and test. Try it with a WAV first of all.

Hope this helps a little.

---

### Post by hillocom on 2007-02-14
thank you so much, tedrogers.

my machine is BTO desktop and the soundcard is audiophile2496 (ice1712/envy24)
 i set it's master clock "s/pdif in" by envy24contorol (alsa-tools-gui)
because i use this device to record the sound from s/pdif out of digital mixer.

Audacity worked very well !! my wav was played normal speed!
but i want this speed on the other apps. 

also, i can't get the sound from the digital mixer so well.
the sound recorded from the mixer isn't slow & low, but very very noisy!

dose ubuntu have its own "sampling rate"?
how can i change it ??

---

### Post by tedrogers on 2007-02-14
Hi,

I'm not sure about setting sample rate within Ubuntu...maybe search for OSS or ALSA tools for this. I don't recall the basic sound control panel having a setting for sample rate.

I assume you have also read this:

[http://ubuntuforums.org/showthread.php?t=333848](http://ubuntuforums.org/showthread.php?t=333848)

If not then it may be useful.

You're 2496 card should be able to handle things fine...but the digital output problems may be something to do with bit depth or too high a level. Try setting everything to standard settings like 16bit / 44.1kHz, as using 24bit / 96kHz could be throwing Ubuntu off track somehow.

The fact that Audacity works fine proves that there is nothing wrong with your 2496 card, it might just be that Ubuntu can't implement its features properly as it is quite an advanced soundcard you have there. My old SB Audigy works just great.

---

### Post by hillocom on 2007-02-14
thank you tedrogers.

the thread you invited me seems useful.
i will study about it more.

by the way, i found new interesting fact.
i played AUDIO CD on ubuntu and checked 
the timer on player app.
then, the timer was ticking slower than
my degital watch !  at the end of the 3 minutes music,
my watch had gone foward by about 10 seconds.

can it be any hints to solve the problem ? :confused:

---

### Post by tedrogers on 2007-02-15
Okay...try using something like the DeMudi distro which is available as a live CD...meaning that you don't need to install it on your HD....you can just run from CD.

[http://www.agnula.info/download/](http://www.agnula.info/download/)

or

[http://linuxtracker.org/torrents-search.php?search=demudi](http://linuxtracker.org/torrents-search.php?search=demudi)

Put some files onto a USB stick that you can play when you boot up DeMudi....this test should tell you whether it is a problem with Ubuntu.

If you can't get Agnula / DeMudi, then try either SLAX, Knoppix, Fedora Core 6 Live versions.

You might also want to try using OSS drivers instead of ALSA.

You may find some useful info here:

[http://linux-sound.org/](http://linux-sound.org/)

This is all I can think of.

---

### Post by hillocom on 2007-02-15
thank you for many useful information.

i guess this problem come from the soundcard setting,
the master clock is "s/pdif in" . because when i set the clock "internal",
music file works well. but, off caurse, i can't get sounds from my digital mixer.

give me the time to study again. i'll seek various possibilities.

thank you so much again, tedrogers! :)

---

### Post by tedrogers on 2007-02-15
That sounds about right to me...using external digital lock could certainly cause a sample rate mismatch, but ideally it shouldn't. I hate those kinds of problems!

Why don't you just set your mixer onto internal sync, then wire your soundcard into the desk using an analogue input? At least this would mean you could use your mixer and have your computers sounds going though it, at least until you find a better solution.

Another solution might be to make your soundcard the master clock source...and have the mixer 'lock to the soundcard'. This might take some re-wiring but should be possible.

What is your setup?

---

### Post by hillocom on 2007-02-16
I'm afraid I can't explain in English well, so let me show [here]("http://www.geocities.jp/hillocom/index.htm")

But as you suggested, it is the best way to use analog I/O and make the soundcard clock internal. 
At least right now.

Anyway,  dose anyone go well on ubuntu with digital input ?
Should I wait for "ubuntu studio" ?

---

### Post by tedrogers on 2007-02-16
I see you have a Roland VM3100 mixer...this brings back nightmare for me as it is a very difficult and unstable mixer to setup with digital sync to the soundcard. I was never able to get it to work effectively and eventually gave up.

For what its worth I think you might be fighting a pointless battle with that VM3100 mixer.

Another thing is you should connected the Edirol speakers to the SPDIF output of your desk and not the sound card...it makes more sense this way.

As for a Ubuntu Studio - I don't when this will be available, but there are other distros that do  this. A very good one (apparently), that has to be paid for, is Studio 2 Go.

---

### Post by hillocom on 2007-02-16
WOW!!    Is VM3100 so terrible ?!
It was an important information to me.
OK, I see,  I re-wire their digital I/O to analog I/O, for a while.

Also "Sound 2 Go !" seems interesting.
I"ll continue to study making music on Linux.

Thank you very much ! :)

---

### Post by tedrogers on 2007-02-16
I just remember the VM3100 being very difficult to use, the operating system is a mess, and the digital lock was unstable. Maybe the one you have is different though, perhaps has newer firmware than the one I used.

Here is an extraction from this website ([http://forum.cakewalk.com/tm.asp?m=734335](http://forum.cakewalk.com/tm.asp?m=734335)):

```

The one really big limitation of the VM-3100 Pro is that it can NOT handle sampling rates greater than 44.1KHz. This can be a real deal-breaker for a lot of people. I have issues with it, myself...but...I have learned to live with it for now. Luckily, it does handle 24-bit processing, which is its saving grace (or else it would be in the dumpster). I really don't mind working in 44.1KHz with 24-bit bandwidth. If I want to work with higher sample rates, I can always fall back on the Delta and use the VM-3100 Pro as an analog mixer. It all works out.

```

If you can get the digital lock working, i.e. the mixer locking to the soundcard, you will need to connect the Edirol speakers to the SPDIF out of the mixer.

Here is a working link to download demudi...not sure if these are the live versions though....the main agnula site appears to be down:

[http://download.mirror.ac.uk/sites/www.agnula.org/demudi/1.2/](http://download.mirror.ac.uk/sites/www.agnula.org/demudi/1.2/)

---

### Post by hillocom on 2007-02-17
I found an  interesting thread in this forum.

[http://www.ubuntuforums.org/showthread.php?t=325074](http://www.ubuntuforums.org/showthread.php?t=325074)

It seems same as my problem, doesn't it ?

---

### Post by tedrogers on 2007-02-17
This would seem to be the same as your problem....and this is made worse by the fact that you cannot change your sample rate on the VM3100 to anything other than 44.1kHz.

It would seem that there is a solution to your problem on that thread - but I looked for 'plughw' in synaptic and it could not be found.

Good luck.

---

