---
title: "sound problem on laptop (no sound)"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Pindulet on 2008-03-11
I have recently installed gutsy on a fujitsu-siemens Amilo pro v2000 laptop and everything seems to be working fine, but i have no sound. I looks like it recognises an audio driver but I hear no sound.
It's really strange because it looks like rythmbox is playing with no problem, but I can't hear any sound. I've tried reinstalling but the problem is still there.
It's an Ubuntu only computer so I would really like to have acces to my music library again.

Here is the lshw output for the audio device:

```

*-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

```

and the output of lsmod | grep snd:

```
snd_intel8x0           34972  3 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

```

Does anyone have some advice on what to do??:confused:

thanks sooooooo much in advance
Kristian

---

### Post by noland on 2008-03-11
i had the same problem, and the solution was pretty stupid (in my case) if you just click once on the volume icon sound is probably at max, but when i double clicked on the same icon, there was another set of volume that was, set to zero... it went to zero for no reason after an upgrade and made me sweat :) good luck!

---

### Post by Pindulet on 2008-03-11
hmm where did you click? I think I have found all the volume controls there is..
As I understand the alsamixer in the terminal i kind of the main soundcontroller. is that right?

anyway thanks for the help

---

### Post by noland on 2008-03-11
yep it came as the alsa mixer, if that didnt work, beats me :) HELP!!!!

---

### Post by forrestcupp on 2008-03-11
noland is talking about the speaker icon in your notification area close to the clock.  If you double click on that, it brings up a GUI volume mixer.

So you've already tried alsamixer in the terminal?  Were all of the applicable volumes turned up?  In alsamixer does it display the correct device?

---

### Post by Pindulet on 2008-03-11
it was worth a shot but no matter how hard I try there doesn't seem to be any extra volume hidden :) 

but thanks anyway...again ;-)

---

### Post by Pindulet on 2008-03-11
ok i have double clicked on that one..
everything is turned up in alsamixer (at least i have tried all possible combinations)

tha alsamixer says:
card: Intel 82801DB-ICH4
chip: Cirrus Logic CS4299 rev 4

that sounds right doesn't it??

---

### Post by Pindulet on 2008-03-11
In the graphical mixer i can choose between 2 devices:
 - Intel 82801DB-ICH4
 - Cirrus Logic CS4299 rev 4

thats odd isn't it when the alsamixer in the terminal says that it's using both?? one as the card and one as the chip...
I don't know much about these things...:confused:

---

