---
title: "Audio Latency in Audacity"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Dannyblueyes on 2008-01-20
I'm running audacity on my Vision Book Laptop by plugging my mixer into my sound card. The first track always records fine but the second and third always lag behind. I'm always having to reline everything which is a real pain in the *** and a crimp in my creative process. To make matters even worse there doesn't appear to be a metronome which would seriously help.

What makes this strange is that when I used to run acid pro on a windows 98 computer with a Pentium 2, 64mb ram, 7 gigs of memory, and a generic sound card I could run up to 10 tracks simultaneously without a problem. Now with a pent 4, 1 gb ram and 160gb of memory I'm having issues with 3. Does anyone have a fix for this?

---

### Post by tgalati4 on 2008-01-20
Are you running a real-time kernel?  Try Dynebolic (dynebolic.org).  It's a live CD with an RT kernel.  You may get better results.  

Also, realize that Audacity is a sound file editor, not a real time audio mixer.  It will do playback during recording of new tracks, but they are lower priority to capturing data so there may be latency.  A faster processor reduces this latency to perhaps acceptable levels for only a few tracks.

---

### Post by Dannyblueyes on 2008-02-15
I tried Dynebolic, and gave it the full benefit of the doubt. I hate to say it, but that software was TERRIBLE. The multitracking software couldn't even handle 2 lousy track of less than 1 minute each. It was incapable of importing a 5 minute Wav file in its entirety. 

I decided to try audacity since it's the most intuitive Linux music software by far. It worked poorly enough in Ubuntu, but in Dynebolic it was even worse. Not only did it also fail to record two tracks in sync, but the second track came out about 2 steps lower than it was recorded. 

Still want to thank you for the suggestion, but I wouldn't recommend this software to my worst enemy.

---

### Post by spiderbatdad on 2008-02-15
[http://www.soundonsound.com/sos/feb03/articles/linuxaudio.asp](http://www.soundonsound.com/sos/feb03/articles/linuxaudio.asp)

---

### Post by luctor on 2008-02-15
get the realtime kernel
install qjackctrl to setup a low-latency [jack]("http://jackaudio.org") audio engine
Use [Ardour]("http://ardour.org") for serious multitrack audio recording, [rosegarden]("http://www.rosegardenmusic.com") could be a good choice too, because it also records midi and has a metronome :-)
I've used [Ardour]("http://ardour.org") to mix 24 tracks of audio on a amd 1700xp processor (1,4 gh) and 768 mb of ram ..
might be a good thing to check out and/or install [ubuntustudio-desktop]("http://www.ubuntustudio.org") (it' s in the apt repo' s)

---

### Post by Dannyblueyes on 2008-02-15
> **luctor said:**
> get the realtime kernel
install qjackctrl to setup a low-latency [jack]("http://jackaudio.org") audio engine
Use [Ardour]("http://ardour.org") for serious multitrack audio recording, [rosegarden]("http://www.rosegardenmusic.com") could be a good choice too, because it also records midi and has a metronome :-)
I've used [Ardour]("http://ardour.org") to mix 24 tracks of audio on a amd 1700xp processor (1,4 gh) and 768 mb of ram ..
might be a good thing to check out and/or install [ubuntustudio-desktop]("http://www.ubuntustudio.org") (it' s in the apt repo' s)

I'm installing rosegarden right now. I'll give it a shot after work. Ardour is the lousy one I was referring to earlier. Really I'm looking for something that's intuitive, hassle free and easy to learn so that I can crank out basic demos, work out harmonies, and that sort of thing. I'll get to the heavy duty professional stuff later.

---

### Post by luctor on 2008-02-15
Be sure to install jackd (qjackctl) if you want to use audio with rosegarden, without jackd rosegarden doesn' t record or play audio.

---

### Post by roaldz on 2008-02-15
I´d dont find ardour lousy.. I LOVE it..:D Just have to get my Realtime jack config working..:(

---

### Post by Dannyblueyes on 2008-02-15
> **luctor said:**
> Be sure to install jackd (qjackctl) if you want to use audio with rosegarden, without jackd rosegarden doesn' t record or play audio.

I ran it briefly this morning before work. It actually asked me to install 5 other programs as well, three of which were not in the applications menu. I finally got to the point where I could record a single track and the program crashed within 10 minutes. 


When you're trying to capture a spontaneous idea or a rough demo you don't need an open source version of pro tools. In fact a program like that can often work against what you're trying to accomplish. 

 I need something that's simple. Plug in the mixer to the sound card, set the input level, create new track, hit record, and GO. In that sense Audacity would be an ideal application if it wasn't for the latency.

---

### Post by roaldz on 2008-02-15
> **Dannyblueyes said:**
> I ran it briefly this morning before work. It actually asked me to install 5 other programs as well, three of which were not in the applications menu. I finally got to the point where I could record a single track and the program crashed within 10 minutes. 


When you're trying to capture a spontaneous idea or a rough demo you don't need an open source version of pro tools. In fact a program like that can often work against what you're trying to accomplish. 

 I need something that's simple. Plug in the mixer to the sound card, set the input level, create new track, hit record, and GO. In that sense Audacity would be an ideal application if it wasn't for the latency.

I´m sorry, but that program you´re looking for might be Ardour.. You can patch your input channels to Ardour, make sure Jackd is running OK and you´re good to go:)

---

### Post by tgalati4 on 2008-02-15
I've made 2-hour, church concert, 2-track stereo recordings using Dynebolic with a PII, 300 MHz, 392 MB of RAM.  What are the specs of your Vision laptop?  What is the output of:

aplay -l

---

### Post by Dannyblueyes on 2008-02-16
> **tgalati4 said:**
> I've made 2-hour, church concert, 2-track stereo recordings using Dynebolic with a PII, 300 MHz, 392 MB of RAM.  What are the specs of your Vision laptop?  What is the output of:

aplay -l

My laptop is a P4 with 1 gb ram. I'm not sure of the mhz rating and I'm not sure what you mean by output. 

As for the recording, I have no problem recording a single track using Audacity. In fact it's a great program for dumping down audio from other sources. I run into trouble when I try to multi track. 

Maybe the best way to do this is to stop banging my head against the wall, buy an old school Hard Disk recorder with a CD burner, and just import everything.

---

### Post by tgalati4 on 2008-02-17
In a terminal, post the output of:

>aplay -l

---

### Post by Dannyblueyes on 2008-02-19
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1

---

### Post by Damiox on 2008-06-09
im having the same problem with ardour...starts to lag with 4 or 5 tracks and a few effects and its not the cpu.... i have a 2.0g processor and 2g of ram...cakewalk did fine on xp with 256m and a 1.6 processor...also ardour wont mix down after about 2 mins....i go to master it and some of the tracks are gone...also jack looses the connection of the lost tracks..i have to manually connect those tracks to the master input....this all should be simpler and ardour should have jack built in and an auto....im plugged straight into the input(not mic) on the sound card from a synth...

and that output..... 

```
damiox@Home-Ubuntu-Main:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

