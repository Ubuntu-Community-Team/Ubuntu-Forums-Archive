---
title: "Sound Problems"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Hawk__0 on 2007-03-30
Hello there, I've used ubuntu several times, but for no longer than a week unfortunately...  I always seem to be unable to configure certain things which drive me to the point of frustration.

I had a post in a different forum and i was telling them about my sound problems and how i wasn't able to use ```
alsaconf 
```anymore.  After hearing that ubuntu has killed it, i read that if my sound card doesn't work... its a bug and i should report it?

Im using a creative Audigy 4 card, and i'm still in the dark as to how i configure it, any help would be great, thanks :D





:popcorn: mmmm:)

---

### Post by Hawk__0 on 2007-03-30
bump

---

### Post by Hawk__0 on 2007-03-30
bump... :(

---

### Post by r4ik on 2007-03-30
Try,

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

Good luck !

---

### Post by Hawk__0 on 2007-03-30
thanks, i have taken almost an identical guide already, but the other one wasnt quite as good, and i get stuck at this step:
```

(4) Now go back to the shell and type
Code:

sudo modprobe snd-

Now, press the TAB key BEFORE pressing the ENTER key to see a list of modules. Try to find the module that matches the driver you found in step 3.


For example, my driver is a via82xx so I would type, sudo modprobe snd-via82xx.

    *

```

If i go to find out what my card is (audigy 4), this is what i find at teh alsa website:
```
Sound Blaster Audigy4 (Non Pro)  	emu10k2
CA0151/P16V 	Details (emu10k1) 	[ANio] [MIDIio] (1) (3)
Mixed reports, so might not work for you.
```

this is my output when i type that command on the step im stuck on (step 4)

```
sgregory@sgregory-desktop:~/Desktop/ktorrent-2.1.1$ sudo modprobe snd-
Display all 151 possibilities? (y or n)
snd-ac97-bus        snd-ens1371         snd-opti93x
snd-ac97-codec      snd-es1688          snd-page-alloc
snd-ad1816a         snd-es1688-lib      snd-pcm
snd-ad1848          snd-es18xx          snd-pcm-oss
snd-ad1848-lib      snd-es1938          snd-pcxhr
snd-ad1889          snd-es1968          snd-pdaudiocf
snd-adlib           snd-es968           snd-rawmidi
snd-ainstr-fm       snd-fm801           snd-riptide
snd-ainstr-gf1      snd-gina20          snd-rme32
snd-ainstr-iw       snd-gina24          snd-rme96
snd-ainstr-simple   snd-gusclassic      snd-rme9652
snd-ak4114          snd-gusextreme      snd-rtctimer
snd-ak4117          snd-gus-lib         snd-sb16
snd-ak4531-codec    snd-gusmax          snd-sb16-csp
snd-ak4xxx-adda     snd-gus-synth       snd-sb16-dsp
snd-ali5451         snd-hda-codec       snd-sb8
snd-als100          snd-hda-intel       snd-sb8-dsp
snd-als300          snd-hdsp            snd-sbawe
snd-als4000         snd-hdspm           snd-sb-common
snd-atiixp          snd-hwdep           snd-seq
snd-atiixp-modem    snd-i2c             snd-seq-device
snd-au8810          snd-ice1712         snd-seq-dummy
snd-au8820          snd-ice1724         snd-seq-instr

```

---

### Post by r4ik on 2007-03-30
Try install alsa-tools

gksudo apt-get install alsa-tools

"A collection of console-based utilities for specific sound hardware:

 ac3dec - A free AC-3 stream decoder
 as10k1 - An assembler for the EMU10K1 (EMU10K2) DSP chip
 sbiload - OPL2/3 FM instrument loader for the ALSA sequencer
 us428control - Controller utility for Tascam US-X2Y"

---

### Post by Hawk__0 on 2007-03-30
```
sgregory@sgregory-desktop:~/Desktop/ktorrent-2.1.1$ gksudo apt-get install alsa-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsa-tools
sgregory@sgregory-desktop:~/Desktop/ktorrent-2.1.1$ 

```



???

---

### Post by r4ik on 2007-03-30
Try Synaptic please.

---

### Post by Hawk__0 on 2007-03-30
it's not in there, i only have "alsa-base" and "alsa-utils" they are both installed already too.

---

### Post by r4ik on 2007-03-30
Try,

[http://www.ubuntuforums.org/showthre...=realtek+sound](http://www.ubuntuforums.org/showthre...=realtek+sound)

if that does not work i am out of ammo.

---

