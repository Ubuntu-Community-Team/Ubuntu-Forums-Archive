---
title: "ALSA makes me want to cry."
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by NinjitsuStylee on 2006-07-05
Hi all. 

So originally I was going to make a post requesting help setting up Skype on my machine, but I've come to realize that I should probably get the simpler stuff out of the way first.

I can't record anything using arecord or Gnome's Sound Recorder program (the latter just crashes, the former only records silence and that's only if I tell it to use the -D plughw:0,0 command, otherwise running just arecord filename.wav by itself just generates a junk .wav file thats around 1.5k in size).

Here's the quick-and-dirty:

[LIST]
[*]Distro: Ubuntu 6.06 (Dapper)
[*]Soundcard: Turtle Beach Santa Cruz (cs46xx)
[*]Listening works quite nicely (you name it, I can listen to it) so ALSA must be configured properly for audio out (I didn't touch anything after upgrading from Breezy to Dapper)
[*]I can hear myself through the speakers when I talk into my mic (when it is unmuted) but it does not "capture"
[*]I have tried messing with every alsamixer setting known to man, so telling me to adjust the alsamixer settings isn't going to help....
[*]...but if you know a specific set of alsamixer settings that does work on the Turtle Beach Santa Cruz then feel free to let me know what it is/post screenshots, and I will try that...although chances are likely that I have already tried them :([/LIST]Seriously, ALSA is so frustrating.  I was originally trying to get MIDI to work and I gave up on that (although timidity decided to work for me randomly one day so I guess that takes care of that), but now I really need to get my microphone to capture properly.

Once again, sound output works great, and I can hear myself through my speakers when the mic is unmuted so something is definitely right....I guess the problem is with the capture settings but I swear I've tried them all.  I just want to be able to use arecord and record a .wav to make sure that things are working.  After that, I will venture into trying to get Skype to work right.

Thanks in advance for your help.

---

### Post by catlett on 2006-07-05
I know you don't want to hear about settings but did you use the terminal based configurer to adjust. Just enter alsamixer in the terminal and press enter ```
alsamixer
``` It will come up in the terminal. Use the arrow keys to move  through the interface. Use "m" (just hit m on the ketyboard) this will toggle the settings on and off. The main thing is to get to is capture all and to the line out settings.
It may also be a root thing. Try launching the applications with sudo and se if it can capture when running as root.

---

### Post by NinjitsuStylee on 2006-07-06
I did use the alsamixer from the terminal and I have everything unmuted, and Mic, Mic1, Capture, and Capture1 set on "Capture" with all volumes at their highest.  

I also tried running arecord as root but still nothing:  recording the file using 

```
arecord -D plughw:0,0 test.wav
```
or
```
sudo arecord -D plughw:0,0 test.wav
```

just gives me a bunch of silence. :confused:

---

### Post by Llurien on 2006-07-06
I have that Turtle Beach thingie.  What made arecord work for me was to use alsamixer to turn on capture on the ADC, put volume on the ADC to near max, and plug the mic into the pink jack.

---

### Post by NinjitsuStylee on 2006-07-08
> **Llurien said:**
> I have that Turtle Beach thingie.  What made arecord work for me was to use alsamixer to turn on capture on the ADC, put volume on the ADC to near max, and plug the mic into the pink jack.


Freakin sweet.  It works.  Thank you.

Now let's see how well Skype works :)

---

### Post by brian g on 2006-07-26
> **Llurien said:**
> I have that Turtle Beach thingie.  What made arecord work for me was to use alsamixer to turn on capture on the ADC, put volume on the ADC to near max, and plug the mic into the pink jack.

not working for me here.
i have mic in pink jack, speakers in green jack and headphones in black.

ADC does nothing for me.. no matter what the skype robot lady can't hear me.

if i mute my 'microphone 1' playback, ALL the sound in my headphones disapears [system, plus mic]

---

### Post by Drakkor on 2006-07-26
Question, how to set capture in terminal alsamixer, playback is default,can't seem to change it. Thanks :-?

---

### Post by NinjitsuStylee on 2006-07-26
> **brian g said:**
> not working for me here.
i have mic in pink jack, speakers in green jack and headphones in black.

ADC does nothing for me.. no matter what the skype robot lady can't hear me.

if i mute my 'microphone 1' playback, ALL the sound in my headphones disapears [system, plus mic]


I don't think having your headphones in the black jack is going to help much...that jack is used for the rear speaker channels, and in Llinux, the TBSC kinda sucks: it wont play front and rear audio at the same time, unless you do some custom scripting with ALSA (or unless you did what I did, whiich was buy a simple stereo splitter adapter and plug both speakers into the green jack...yay engineering).

As far as the Skype lady, what I would suggest is you make sure you have ALSA properly configured first (Ii'd check out some of the other forum threads here) and then make sure you have capture set on both the ADC and mic channels (and Mic1 if you want, I'm not sure if it matters but I have it set).  Also make sure your volumes are up and whatnot.

---

### Post by Handyman's Special on 2006-07-26
> **NinjitsuStylee said:**
> . . . . I was originally trying to get MIDI to work and I gave up on that . . . .

Me, too! From there I *tried* to get java applets to work on my Firefox browser - giant fiasco that turned out to be.

The thing is driving me nuts. I have been going at this for over 3 weeks. Too much of my life is being wasted on what now appears to be a 'virtual boat.' ie: Boat = a hole in the water, surrounded by wood that your pour your time and money into.

I am close to giving up on Ubuntu. ](*,) 

HS

---

### Post by brian g on 2006-07-26
> **NinjitsuStylee said:**
> I don't think having your headphones in the black jack is going to help much...that jack is used for the rear speaker channels, and in Llinux, the TBSC kinda sucks: it wont play front and rear audio at the same time, unless you do some custom scripting with ALSA (or unless you did what I did, whiich was buy a simple stereo splitter adapter and plug both speakers into the green jack...yay engineering).

As far as the Skype lady, what I would suggest is you make sure you have ALSA properly configured first (Ii'd check out some of the other forum threads here) and then make sure you have capture set on both the ADC and mic channels (and Mic1 if you want, I'm not sure if it matters but I have it set).  Also make sure your volumes are up and whatnot.
black plug was the only one i could get any output from without having to unplug jacks and re-plug jacks.

maybe i should start looking for a new sound card

---

### Post by catlett on 2006-07-26
This may help. [http://www.ubuntuforums.org/showthread.php?t=205449&highlight=floppy+mount](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=floppy+mount)
If you are experienced with Linux, the gentoo guide on any subject  is a great resource. Because you configure everything from scratch in gentoo, their guides cover the entire process, You might be able to find a section that deals with your specific issue. [http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#The_dmix_device](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#The_dmix_device)

---

### Post by NinjitsuStylee on 2006-07-26
> **Handyman's Special said:**
> 
I am close to giving up on Ubuntu. ](*,) 
HS

Don't give up yet! 

Personally I think it's just the TBSC that's crap, not Ubuntu or Linux itself.  I would've said otherwise during my first few weeks with Ubuntu (and linux in general) but now it's pretty clear to me that there's no chance I'd give up my 'nix :)

I ended up getting some level of midi to work (using the timidity software), and all I really needed it for was so that I could hear my guitar tablature being played back...and I managed to get that work (thru extensive documentation reading, unfortunately), so I'm pretty satisfied with everything now!

---

### Post by NinjitsuStylee on 2006-07-26
Good call catlett.....I find myself frequenting the Gentoo wiki a lot these days :)

---

### Post by sbooth on 2006-09-02
> **brian g said:**
> not working for me here.
i have mic in pink jack, speakers in green jack

Not working for me either - and driving me completely nuts.  I'm trying to get TeamSpeak 2 working (for nothing more exciting than listening to a baby monitor when I'm at my machine in the shed across the garden... too far for the radio range of the baby monitor).

Installed the server on one of our servers in the shed, installed the client on a WinXP box and also on my Ubuntu laptop... and could hear everything fine.  Installed the client on my Ubuntu desktop in the shed - Dapper, Turtle Beach Santa Cruz (hence my reply in this thread) - could hear what was going on in the house (which is what I wanted), could hear myself talk into the mic through the speakers... but TeamSpeak couldn't detect anything in the mic.

Sound recorder in Gnome crashes, arecord doesn't record anything.

I've played with alsamixer, followed howtos... and now can't hear what's going on in the house let alone get the mic working.

It's driving me completely potty - and now I'm thinking I'll have to apt-get remove the whole alsa thing and reinstall it since it's in a mess.

Any suggestions would be very much appreciated.

---

