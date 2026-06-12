---
title: "Screwy Audio Questions..."
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by hseiken on 2007-07-02
Hey, trying to get into the Ubuntu thing and I have a couple of questions:

I'm using an Acer TravelMate2450 laptop with the built in HDAudio somethingoranother...heh...

Anyway, the audio works really strange on this system.  After startup, to get sound out of both left and right channels on any program, I have to turn the volume all the way down in the mixer then back up.  

Next, Jack doesn't work claiming problems with the ALSA drivers:

creating alsa driver ... hw:1|-|1024|2|44100|0|2|nomon|hwmeter|-|32bit
control device hw:1
control open "hw:1" (No such device)
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
no message buffer overruns
07:37:00.435 JACK was stopped successfully.
07:37:00.435 Post-shutdown script...
07:37:00.435 killall jackd
jackd: no process killed

I'm almost positive I've used an ALSA supported sound program before, so I don't understand that one at all...

Basically, my question is can someone help me get these problems sorted out?  I'm not quite sure where to go to make sure my audio device is up to date on it's drivers, and more important, what I need to do at the ALSA site to make sure I've got everything on that end loaded properly and up to date.  

I'm, quite honestly, not adept at all with Terminal commands, so if you have some that i can use to check states of different properties so I can provide you with more usable information, please, by all means, provide and I will give feedback.  

Thanks for all the help in advance.  

HS

---

### Post by Pragmatist on 2007-07-02
> **hseiken said:**
>   After startup, to get sound out of both left and right channels on any program, I have to turn the volume all the way down in the mixer then back up.  
By channels I assume you mean the left and right speakers, right?  Do you do this right after startup?  What happens if you wait 15 minutes?

> **hseiken said:**
> Next, Jack doesn't work...
Did you start Jack?  What applications are you running that use Jack?

Has your sound card worked in Ubuntu before?  How about other Linux distributions?

---

### Post by hseiken on 2007-07-02
Yes, I have audio, and yes, ALSA works (I'm using PD right now and sound is routed to the ALSA system).  

Jack does start, but again, it says that ALSA is not cooperating.  No audio applications are open when I start Jack.  

Out of curiosity, what would waiting 15 minutes after startup solve?  Once I'm logged into to Ubuntu, I want to start playing with audio.  

And to your assumption about left and right speakers, you are correct.  It's a very strange problem.  However, I just noticed this morning that my audio mixer has selections for ALSA and OSS.  ALSA seems to start up with both channels activated, however, OSS doesn't.  Is there a way to default to ALSA?  That may solve my problem...i've also heard that many programs are moving away from OSS support anyway...

Thanks for your time.

---

### Post by hseiken on 2007-07-07
Here is a verbose output of Jack Control when I start it (again, no audio programs are running, I've searched the forums and turned off system sounds to see if that would work, so these are the things I've tried but to no avail)

```


10:52:49.603 Patchbay deactivated.
10:52:49.641 Statistics reset.
10:52:49.660 JACK is starting...
10:52:49.661 /usr/bin/jackd -v -dalsa -dhw:0 -r44100 -p1024 -n2 -P/dev/dsp -o2 -M -O4
10:52:49.682 JACK was started with PID=6085 (0x17c5).
10:52:49.698 MIDI connection graph change.
getting driver descriptor from /usr/lib/libjack0.100.0/jack_alsa.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_oss.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_dummy.so
getting driver descriptor from /usr/lib/libjack0.100.0/jack_freebob.so
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
loading driver ..
apparent rate = 44100
creating alsa driver ... /dev/dsp|-|1024|2|44100|0|2|nomon|hwmeter|-|32bit
ALSA lib control.c:910:(snd_ctl_open_noupdate) Invalid CTL /dev/dsp
control open "/dev/dsp" (No such file or directory)
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via gettimeofday
required capabilities not available
capabilities: =
new client: alsa_pcm, id = 1 type 1 @ 0x805adf8 fd = -1
starting server engine shutdown
freeing shared port segments
stopping server thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
no message buffer overruns
cleaning up shared memory
cleaning up files
unregistering server `default'
10:52:49.714 JACK was stopped successfully.
10:52:49.714 Post-shutdown script...
10:52:49.714 killall jackd
jackd: no process killed
10:52:49.890 MIDI connection change.
10:52:49.923 Post-shutdown script terminated with exit status=256.
10:52:51.931 Could not connect to JACK server as client. Please check the messages window for more info.

```

The thing is, I want to do a 'fresh' install of Jack Audio Connection Kit from their site, but there's no repository of their program listed to add to synaptic.  Installing the GUI version of jack seems to install jack as well since when I type jackd in terminal, it gives me the 'okay, no what, smart guy?' list of command line peramters.  Other things I've tried (on the Jack GUI version) are setting different cards, different methods (OSS, etc.) and all of them come up short of working.

REALLY need this to work.

---

### Post by Pragmatist on 2007-07-07
> I want to do a 'fresh' install of Jack Audio Connection Kit from their site, but there's no repository of their program listed to add to synaptic.

The Ubuntu repositories have the jack packages.  Please post this file so we can make sure you have the right repositories enabled: [B]/etc/apt/sources.list

[/B]I'm still not sure what your other problems are.  Does ALSA work?  What happens when you don't use jack?  What do you need jack for?  What applications are you using that require it?

Have you considered upgrading to Ubuntu Studio?
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

---

### Post by Pragmatist on 2007-07-07
How did you install jack?

---

### Post by hseiken on 2007-07-07
I used the add/remove programs list (not the basic synaptic package manager)...one of the included download/installs for it IS jack...

And yes, ALSA works fine, though I have some problems with it disappearing sometimes...speaking of which, how would I go about reinitializing the entire sound environment as if it's a fresh boot without rebooting?  Just a side note...I'm testing lots of different audio apps right now...


As far as Ubuntu Studio, I don't have a DVD burner...the iso is too large for a CD, last I checked...the closest I can get is Pure:Dyne which I've tried and it's not quite as nice to my laptop as Ubuntu is.  Graphics problems is one of the issues with it that I just don't have the patience to deal with...

---

### Post by Pragmatist on 2007-07-07
> **hseiken said:**
> ALSA works fine...
Great!  So this post has been narrowed to a problem your having with jack.


 > **hseiken said:**
> how would I go about reinitializing the entire sound environment 
The only way I know of is to do a "complete uninstall" of each application and then reinstall each application.  I wouldn't, however, advise doing that unless you really know what your doing.

Have you considered using CCRMA (Although you do need to use it with Fedora, you might find the instructions useful):
[http://ccrma.stanford.edu/planetccrma/software/](http://ccrma.stanford.edu/planetccrma/software/)

There are many useful guides on jack.  You can search for them with google.  Realize that there is a learning curve for advanced sound work on Linux.  I have gotten jack to work in the past, but it took some time, and patience, to set it up.  To solve your problem find a guide.  Follow the instructions in the guide, and then, if you have problems with specific steps, please create a thread and we will help you with them.

---

### Post by hseiken on 2007-07-07
It seems maybe ubuntu isn't fully recognizing my card...or maybe it's drivers aren't working properly.  As a comparison (I still have the single channel audio glitch on startup that requires turning the volume all the way down then back up to get stereo), I test drove a live cd of linux mint.  The audio worked fine and defaulted to alsa even.  

However, due to it BEING a live CD, I have to install it to find out if Jack has similar problems.  But at the same time, I see it as one of the problems solved...it's built on Ubuntu, and is still linux, so in that respect, I don't feel like I'm moving 'back' to anything (i.e. to windoze).  

I'm really not in the patient mood right now for figuring out what is wrong because I ended up accidentally wiping out my windows partition with a factory restore (was in no part Ubuntu's fault, btw...was operator error...I had been using ubuntu for a while and forgot which of the windows options was the one to boot windows...and chose the wrong one...to quote the knight from Indiana Jones and the Last Crusade..."He chose....poorly."

So I'm going to give Linux Mint a spin.  BTW, I did get Jack working in OSS mode, but then CheeseTracker didn't want to use it for sound for some reason...even though it allowed me to enable it (jack) as a sound source (finally)...so I can work it, but again, wouldn't ALSA be better under jack anyway?  

I don't know...I'll probably ponder everything tonight and take action on my decision tomorrow.

---

### Post by hseiken on 2007-07-07
On second thought, actually, I want to muscle my system to perfect operation...

So forget jack...

I will deal with that later...

My first order of business...

I just noticed this...and it may be the root of everything wrong...



Every other boot, the 'Volume Applet' that is defaulted to sit in the toolbar next to the date shows ALSA available in addition to OSS...every other time, it's just OSS.  Eventually, after running programs a couple of times (sound progs, btw), ALSA will disappear from devices available in the applet.  

This is leading me to believe that ALSA isn't configured correctly or isn't installed correctly or that maybe even something else is wrong.  If Mint can see it and default it AND get stereo audio from a LIVE CD, that means that it IS possible to get this working on Ubuntu as well.  

So with those diagnostics, I also provide my card info.

It's hard wired onto my acer and goes by the name:  Realtek HD 883 (this is what OSS 'sees'.  I know that it has the brand and 'type' (HD) correct...so maybe I should investigate there first to see if the correct sound drivers are running?  

Hmmm...suggestions on where to start?

---

### Post by Pragmatist on 2007-07-07
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by hseiken on 2007-07-09
Great!  I will give these a try!  Will let you know how it turns out...got to sleep now!

---

### Post by hseiken on 2007-07-10
Okay, well one problem down, 1 to go...

The ALSA driver works properly now (no single channel on reboots, and it's ALWAYS there on reboots instead of every other one)...next up, I just gotta figure out jack...

Thanks for that link, that was super awesome.

---

### Post by hseiken on 2007-07-10
I'm going ahead and upgrading to ubuntu studio to see if that will get jack to work.  

Im mostly interested in jack for use with energyxt2...It supports both, so I want to check it out with the lower latency.  BTW, before I restart...will grub be updated to reflect the ubuntu changes?  If not, how would I go about doing that?  

Sorry for all the questions.  I'm new to the linux world and multiboots, etc...

I'm all for learning, but I'm also kind of cautious.  ;)

---

### Post by hseiken on 2007-07-14
okay, now my problem is, i'm not getting the duplex abilities of my card...actually, i'm not getting *ANY* recording abilities...not even sure how to tackle this problem...I could play one program in windows and record with audacity the output of the entire soundcard...in ubuntu, i can't even select the microphone to record from...i'm not sure what to do!  any help is appreciative...and this is after compiling alsa for my card.

---

### Post by Pragmatist on 2007-07-14
> **hseiken said:**
> okay, now my problem is...
What happened with jack?
> **hseiken said:**
> ...i'm not getting *ANY* recording abilities...any help is appreciative...
You will probably get more success if you make a separate thread for this  new problem.

---

### Post by hseiken on 2007-07-15
At the moment, I don't need jack, so I'm not sweating over that issue for now.  :)

---

