---
title: "Help no sound"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by nwr222 on 2007-02-07
I have just installled kubuntu for the first time.  I am having some problems getting any sound at all.  I have referred to the doument "Comprehensive Sound Problems Solutions Guide".  The system seems to see the sound card OK.

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Value [CT4871]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
...
$ cat /proc/asound/modules
 0 snd_emu10k1

$ asoundconf list
Names of available sound cards:
Live

I have run alsamixer and unmutted everything, and set the level of everything to maximum.

I have tried playing a CD and and MP3 file - not a peep out of anything.

---

### Post by ^rooker on 2007-02-07
1) Which application have you used for CD/MP3 playback?
2) Please make sure that all audio cables are connected correctly... I know this always sounds offending, but even after *years* of working with technical equipment this one is among the top 10 reasons for things to go wrong.


3) If your soundcard supports surround (e.g. 5.1) you often can switch inputs and outputs (e.g. LineOut,LineIn,Mic >>> Front,Rear,CenterWoofer)
Check that with alsamixer

---

### Post by xpod on 2007-02-07
You might need to install the required codecs for mp3 and the like

[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

You could also use a program called Automatix2 which will give you all your codecs for music and movies as well as a couple of dozen other handy applications that you`ll most likely want 
such as your flash,java,p2p,media players and a lot more besides

[http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

Of course if it`s an actual problem with your sound card then thats another matter:( 

Good luck regardless

---

### Post by nwr222 on 2007-02-07
I am using gxine.
I am pretty sure that the cabling is correct - it works just fine under *cough* XP.

---

### Post by nwr222 on 2007-02-07
I worked it out with a clue from the guide mentioned above.  Thinking I was covering all my bases I had set everthing on and everthing max in alsamixer.  When I had a closer look one of the options I had unmuted was "Optical Raw".  I don't have an optical connection onto the soundcard.  When I set that option to mute my CD plays.  :)  Still no MP3, but thats a problem for tomorrow night.

---

### Post by gentlemanmasher on 2007-02-07
Do you have onboard sound and a sound card?

---

### Post by nwr222 on 2007-02-09
I only have a sound card.  With the help above I also have MP3 working now, so it's all going well and I am enjoying the experience.

---

