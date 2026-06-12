---
title: "Sound doesn't problem (Natty)"
date: 2011-05-15
forum: Apple Hardware Users
---

### Post by MizoZ on 2011-05-15
Hello,

I finally upgraded to Ubuntu Natty Narwhal, everything works fine except Sound. It doesn't work. Could someone help me to solve this problem ?

here's some informations :

iBook G4 (1.3Ghz)

- lsmod |grep snd 
```
snd_aoa_codec_tas      11781  2 
snd_aoa_fabric_layout    10362  2 
snd_aoa                16332  2 snd_aoa_codec_tas,snd_aoa_fabric_layout
snd_aoa_i2sbus         19627  1 
snd_seq_midi            5492  0 
snd_rawmidi            21923  1 snd_seq_midi
snd_seq_midi_event      7179  1 snd_seq_midi
snd_powermac           66253  0 
snd_seq                57836  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                84085  2 snd_aoa_i2sbus,snd_powermac
snd_timer              23210  2 snd_seq,snd_pcm
snd_seq_device          6870  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_page_alloc          7313  1 snd_pcm
snd                    59925  14 snd_aoa_codec_tas,snd_aoa_fabric_layout,snd_aoa,snd_aoa_i2sbus,snd_rawmidi,snd_powermac,snd_seq,snd_pcm,snd_timer,snd_seq_device
soundcore               1148  1 snd
snd_aoa_soundbus        4824  2 snd_aoa_fabric_layout,snd_aoa_i2sbus

```- cat /proc/asound/cards
```

0 [SoundByLayout  ]: AppleOnbdAudio - SoundByLayout
                      SoundByLayout

```- dpkg -l | egrep "(alsa-|asound)"
```
ii  alsa-base                             1.0.24+dfsg-0ubuntu1                       ALSA driver configuration files
ii  alsa-utils                            1.0.24.2-0ubuntu6                          Utilities for configuring and using ALSA
ii  libasound2                            1.0.24.1-0ubuntu5                          shared library for ALSA applications
ii  libasound2-plugins                    1.0.24-0ubuntu2                            ALSA library additional plugins

```- aplay -lL
```
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=SoundByLayout,DEV=0
    SoundByLayout, 
    Front speakers
dmix:CARD=SoundByLayout,DEV=0
    SoundByLayout, 
    Direct sample mixing device
dsnoop:CARD=SoundByLayout,DEV=0
    SoundByLayout, 
    Direct sample snooping device
hw:CARD=SoundByLayout,DEV=0
    SoundByLayout, 
    Direct hardware device without any conversions
plughw:CARD=SoundByLayout,DEV=0
    SoundByLayout, 
    Hardware device with all software conversions
**** List of PLAYBACK Hardware Devices ****
card 0: SoundByLayout [SoundByLayout], device 0: Master []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Regards.

---

### Post by MizoZ on 2011-05-15
By the way , when I tape "lspci" there's no sound controller :s

And when the computer boot's up I can hear a tone.

---

### Post by linuxopjemac on 2011-05-15
Maybe this helps:
[http://oswaldkelso.blogspot.com/2010/10/how-to-fix-no-sound-on-debian-powerpc.html](http://oswaldkelso.blogspot.com/2010/10/how-to-fix-no-sound-on-debian-powerpc.html)

---

