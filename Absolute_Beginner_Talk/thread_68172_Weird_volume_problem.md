---
title: "Weird volume problem"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-09-22
I seem to have trouble adjusting my volume.

My sound effects are comming out fine and can be adjusted with the slider and pcm volume. However when i go to say a flash prog with sound its deafening at full volume. I seem to have 2 mixers Alsa and Oss whatever that means. Isnt there just one master volume control?? as its really annoning having to mute one, change device and then mute the other,

Before anyone asks there is only one soundcard and thats onboard ac97? i think

---

### Post by Kapre on 2005-09-22
[QUOTE=dgrafix]I seem to have trouble adjusting my volume.

My sound effects are comming out fine and can be adjusted with the slider and pcm volume. However when i go to say a flash prog with sound its deafening at full volume. I seem to have 2 mixers Alsa and Oss whatever that means. Isnt there just one master volume control?? as its really annoning having to mute one, change device and then mute the other,

Before anyone asks there is only one soundcard and thats onboard ac97? i think[/QUOTE]

dgrafix - try playing mwith your mulimedia systems selector and use combinations on your input and output plugin (use OSS & ESD or ESD & OSS or whatever plugin that you have).

K

---

### Post by syväpaahto on 2006-01-16
bump. Did anyone solve this? I have the same onboard card and no volume control. Multimedia Systems Selector just crashes if I try anything other than OSS

---

### Post by syväpaahto on 2006-01-16
this is what i found out so far... 

I should configure a software volume control for ALSA by creating a ~/.asoundrc file and putting this in it:

```
pcm.name {
        type softvol            # Soft Volume conversion PCM
        slave STR               # Slave name
        # or
        slave {                 # Slave definition
                pcm STR         # Slave PCM name
                # or
                pcm { }         # Slave PCM definition
                [format STR]    # Slave format
        }
        control {
                name STR        # control element id string
                [card STR]      # control card index
                [iface STR]     # interface of the element
                [index INT]     # index of the element
                [device INT]    # device number of the element
                [subdevice INT] # subdevice number of the element
                [count INT]     # control channels 1 or 2 (default: 2)
        }
        [min_dB REAL]           # minimal dB value (default: -48.0)
        [resolution INT]        # resolution (default: 256)
}
```
but I'm too linux nooby to fill the blanks (ie. SRT and INT). any hint where to get those values?

---

### Post by syväpaahto on 2006-01-16
well I got it working by creating a /etc/asound.conf with this content:
```
pcm.snd-hw {
  type hw
  card 0
}

ctl.snd-hw {
  type hw
  card 0
}

pcm.!default {
  type plug
  slave.pcm "snd"
}

pcm.snd {
   type softvol
   slave {
      pcm {
         type dmix
         ipc_key 1234 # any number
         slave {
            pcm "hw:0,0"
            rate 44100
            period_time 0
            period_size 1024
            buffer_size 4096
         }
      }
   }
   control {
      name "hw"
      card 0
   }
}
```
It created a new bar on alsamixer and gnome-volume-control. I now can finally change the volume. I created the code part by part using google without mutch understanding what I'm doing, so I have no idea if it's 100% ok

P.S onboard sound is C-Media 9739 AC97

[EDIT: ah crap! I have seemed to post the last 3 post on the wrong thread. I ment this to go on the topic about volume change not working. sry

ment it to go here
[http://www.ubuntuforums.org/showthread.php?t=87599&highlight=softvol+bugzilla](http://www.ubuntuforums.org/showthread.php?t=87599&highlight=softvol+bugzilla)

---

