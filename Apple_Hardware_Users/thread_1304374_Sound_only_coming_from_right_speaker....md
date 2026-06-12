---
title: "Sound only coming from right speaker..."
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by sebovzeoueb on 2009-10-29
OK, now I know this subject has been brought up many times, but I am just looking for a straight answer (having been unable to find one). After much fiddling around I have managed to get sound coming out of my MacBook Pro 5.2... however using the built in speakers, sound only comes from the right hand one. Headphones work fine.

So, this is my question: Is it possible to get stereo sound out of the built in speakers of the MacBook Pro 5.2 in Ubuntu Jaunty? Yes or No?

If yes, would someone be able to point me in the direction of a fix which can be executed by someone who knows very little about Linux (i.e. Me). As in, doesn't assume any prior knowledge of terminal commands etc.

For those of you still trying to get some sound, the thing that seemed to fix it for me was typing:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```and adding
```
options snd-hda-intel model=mb5
```at the end of the file

I did also upgrade my alsa drivers to 1.0.21 before doing this, but not sure if that was necessary.

But as mentioned above, my sound only comes from headphones and right hand speaker. The speaker output seems to be controlled by the "Side" channel of the mixer. Any ideas for a fix?

Tried this: [http://ubuntuforums.org/showpost.php?p=7377913&postcount=5](http://ubuntuforums.org/showpost.php?p=7377913&postcount=5) but the applet mentioned does not show up, and my sound is exactly the same as before. Then I noticed its for 64bit, and I am running 32bit...

---

### Post by sebovzeoueb on 2009-10-29
I ran a speaker test, not sure if this is of any help:
```
speaker-test 1.0.21

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 10.947507
 0 - Front Left
```
At some point previously it used to show 6 channels... not sure what has happened here. The "Front Left" speaker does however cause sound to come out of the right hand speaker.

---

### Post by sebovzeoueb on 2009-10-29
OK, to update on the situation, I have installed Ubuntu 9.10, and I can confirm that sound is coming out of both speakers now, I had to go into alsamixer and set number of channels to 4 (I'm seeing some different options on my mixer compared to the one I had in 9.04). I also edited the alsa-base file with the mbp3 option. Further tests when it is not too late at night to "crank" the speakers. Let's see if issues such as lack of "bass" mentioned in bug reports concerning this problem have been resolved. Will update further should there still be problems...

---

### Post by CosyCat on 2009-10-29
Yes I also have lack of "bass"

---

### Post by sebovzeoueb on 2009-10-30
OK, having now been able to do a louder test, I have managed to establish that instead of "mpb3" if I change the last bit of my alsa-base file to "mb5" my speakers seem to be working correctly, so like my original post in fact. I think I had used mbp3 as that was the one most people seemed to be using, but mb5 works much better. Sound card shows up as 6ch now and if I do speaker-test -c6 I get noise from every speaker other than LFE, but when listening to a video on Youtube the sound seems normal. 
CosyCat, have you tried doing the alsa-base modification? And fiddling around using alsamixer?

---

### Post by CosyCat on 2009-10-30
Yes I set line 
options snd-hda-intel model=mb5 and fixed some of the problem in alsamixer

but the "bass" is lacking not as good as in OSX

---

### Post by volanin on 2009-11-01
In the terminal, type:

```
$ alsamixer -c0
```

And unmute everything except IEC958!
This should fix it.

---

### Post by crazycatlady0 on 2009-11-10
> **volanin said:**
> In the terminal, type:

```
$ alsamixer -c0
```And unmute everything except IEC958!
This should fix it.


this command fixed my problems.  I didn't have to change any of the muting.

Many thanks!

---

### Post by A0MiKon on 2009-11-11
> **volanin said:**
> In the terminal, type:

```
$ alsamixer -c0
```And unmute everything except IEC958!
This should fix it.
I had somewhat the same problem with my pc, with only the center speaker working. Tried this and turned up the volume on all channels and my problems are gone.
Thank you volanin! :D

---

