---
title: "Microphones dead"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by YoungCthulhu on 2007-04-08
Hello,

I have never been able to get any microphones to work with this computer, (or the last one, or the one before that...)  Now I want to use the mic and an old webcam to talk to my dad in NZ so need to fix this problem.

I have a new box with a Core2 Duo Intel E6400 CPU and a GIG 9VM900M motherboard.  I am fairly sure the "sound card" is handled by the motherboard.

I have been reading other peoples' problems and mine seems to be similar, viz:

[LIST]
[*]Applications | Sound & Video | Sound Recorder does not pick up any sound.  I have tried this with 3 different mics now and the same thing happens.
[*]System | Preferences | Sound | Sound Capture just produces static in the speakers 
[/LIST]


> stuart@GORT:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
stuart@GORT:~$ cat /proc/asound/modules
 0 snd_hda_intel
stuart@GORT:~$ grep 'audio' /etc/group
audio: x:29:stuart
stuart@GORT:~$ 

I have made sure that sound capture is turned up fully using alsamixer and also by double clicking the sound icon on the desktop.

Do I need to get a dedicated sound card for this machine, or is there something else I should be doing?

Cheers

---

### Post by rajeev1204 on 2007-04-08
HI

right click on volume icon in panel > open volume control >edit preferences > select microphone .

see if that is on mute . This is different from capture option . 

So check if both are on and max.

---

### Post by YoungCthulhu on 2007-04-08
Thanks Rajeev1204,

One problem though: I followed your instructions, but when I get to "open volume control | edit | preferences | select tracks to be visible" (box) microphone is not there, just master, PCM or capture.  Capture is set to max and un-muted.

I get the same 3 alternatives in terminal using alsamixer too.  Not all that surprising really, even to a beginner...:) 

Thanks for your interest and help so far
Cheers

---

### Post by rajeev1204 on 2007-04-08
What kind of mic u having?  plugged in properly i assume .

Anyways  --- try to remove and replug the mic in the (red ? ) color socket and then again check for microphone in preferences in volume control. 

Also i believe the microphone option is available whether or not a mic is detected .
I mean within open vol control >edit preferences. 

Could u check again please?


Update --- oops i couldnt hear anything in sound recorder either . Works fine with skype though.


U checked with skype?

regards

rajeev

---

### Post by rajeev1204 on 2007-04-08
Ok got it

Just enable capture from preferences ( not capture 1 and 2) and after recording , select save as option in file menu . Dont forget microphone option too in preferences

Pressing  save option doesnt seem to save it . Do a save as --filename  to save the recording

---

### Post by YoungCthulhu on 2007-04-12
Thanks for that, still no joy :( 

I made sure that it is plugged in to the right hole, and experimented with plugging it in to the wrong holes too and it doesn't work.  

Any ideas, is it my sound card integrated with the mother board that needs a better driver, or a separate PCI sound card?  I have never been able to get more than 3 channels displayed using alsamixer, the old broken computer that this one replaced showed up at least 6 channels.

Thanks for your help so far, go and get yourself a beer now and charge it to me!

---

### Post by Valstorm2323 on 2007-04-12
My microphone doesnt work with that recorder either!

I can hear myself but skype test isn't recording my voice. I mean I know it's not beautiful but come on, no need to insult a guy! :s

Anyways that aside, I've been trying to get it to work on skype but seems pointless.

---

### Post by odzx on 2007-04-14
I have the same problem. if you looked through the forum you probably seen this already. i have the same card as you and i actually got it to record sound, and have all the channels in 'volume control' and 'alsamixer', buy compiling the last alsa  (1.0.14rc2).
there are instructions on this forum if you want to try it. however, doing this did not go perfect for me. the new alsa changed some of my sound configurations, that i did not know exactly how to change back, and for some reason i lost sound in flash animations with Firefox and could not get it back, no matter what i did.
i just installed feisty a few days ago (fresh install) and the same thing happens (no mic, only three channels). testing some other live cds gave me the same results (knoppix, mandriva, gentoo, simplymepis) i dont want to have to choose between flash sound (and some other things) and being able to use my mic...
anyway since i don't recommend recompiling alsa the way i did, i guess  this reply at least tells you that the problem is not your sound card.
hopefully someone can give us hint how to make alsa to work or to compile without messing up anything else...:confused:

---

### Post by leodp on 2007-04-18
> **Valstorm2323 said:**
> My microphone doesnt work with that recorder either!

I can hear myself but skype test isn't recording my voice. I mean I know it's not beautiful but come on, no need to insult a guy! :s

Anyways that aside, I've been trying to get it to work on skype but seems pointless.


Hi, I had the same issue with Skype, and could solve it.
To do this I have to enable some stuff on the audio, that I usually do with kmix. I have a SiS SI7012 card, but something similar may apply to you too.

When I open kmix mixer, go to the Input tab and:
1) enable  the Microphone record (red button) and put the volume to maximum
2) enable capture  (red button) and put the volume to maximum

Then on the Switches tab:
1) Select "Mic boost (+20dB)"
2) On  the "Mic Select" I choose "Mic1" and NOT "Mic2"

The remaining switches (red and yellow buttons) seem ineffective in in regard to mic capture, I disabled all of them, and set:
Surrond jack mode            to   Shared
IEC958 Playback source   to     AC-Link
Mono output Select           to     Mix
Channel mode                   to     2ch
DAC Clock Source            to     AC-Link

With this setting "Skype" is working, and with "rec test.wav" I can capture all the noises of my PC fan :D 
Hope that helps.

Ciao, Leo

---

### Post by strangedata on 2007-05-11
Hi,

I've tried almost everything that should be done to get mic working. Actually, after googling it a bit, I performed at least 8 different methods.

With that I got my HDA VIA VT82xx to record on Sound Recorder, but other applications, like Gizmo, cannot use the microphone.

I can also hear myself speaking, but the application (apparently) cannot.

I'm new to sound issues, so I don't know what log/info would help to pinpoint the problem. If you can help me, please tell me what I need to post here.

Thanks a lot! Any help will be greatly appreciated!

---

### Post by icechen1 on 2007-05-11
My microphone don't work.
I think this is a bug with ALSA.

---

