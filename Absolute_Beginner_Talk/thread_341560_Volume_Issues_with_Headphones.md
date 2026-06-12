---
title: "Volume Issues with Headphones"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Neil Goodman on 2007-01-18
Hello,

I have an Inspiron 6000 notebook running Ubuntu 6.10. I use amaroK to listen to music, which works out fine, except when I use headphones. The Volume Applet seems to only control the volume of my laptop's speakers, but not the headphone port. 

I can adjust the volume using the volume control in amaroK. That is a slight annoyance that I can deal with, but I would still like to know if there is anyway to have the Volume Applet control the volume for the headphone port.

Thanks.

---

### Post by j19sch on 2007-01-24
I have little experience with KDE, but the Volume Applet probably controls the 'Line out' volume, not the 'Headphone out' volume. So you could try to google for a KDE Headphone Volume applet or go to main volume control in KDE to set the headphone volume.

Joep

---

### Post by g3k0 on 2007-01-24
Hmmm I have the same problem....

---

### Post by healthpellets on 2007-01-24
I've had this same problem for a while.  I'm using a Toshiba L35 series and cannot get volume out of the headphones for anything.  

I've used Ubuntu and Kubuntu.  No difference.

It appears to be a problem similar to the wireless card issue:  it affects some, but not others.  And those it does affect can either easily resolve it, or have no luck (like me).

So I guess good luck to you...and if you find anything out, please let the rest of us know.

---

### Post by Thisbetom on 2007-04-01
[http://www.ubuntuforums.org/showthread.php?t=255586](http://www.ubuntuforums.org/showthread.php?t=255586)

Basically you need to adjust the headphone volume separately from the speaker volume

To do this make sure you have a volume contro icon on your panel... If not Right click on the panel > Add to Panel > Select Volume Control.

Right Click on the volume control icon in the panel and select Open Volume Control.

Adjust the volume as needed

-Tom

---

### Post by ac7ss on 2007-04-01
I use the xfce4-mixer and there is a control for the headphone on that .

Try amixer, the man page says you can set any setting that way.

run it by itself and see if it can read your card.

Mine returned:
```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 14 [45%] [on]
  Front Right: Playback 14 [45%] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 22 [71%] [on]
  Front Right: Playback 22 [71%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [off] Capture [off]
  Front Right: Playback 0 [0%] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [on] Capture [off]
  Front Right: Playback 25 [81%] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Video',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Phone',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 0 [0%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Aux',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [on]
  Front Right: Capture 0 [0%] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

```

so I did this:
```
$ amixer sset Headphone 80%
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [on]
  Front Right: Playback 25 [81%] [on]

```

Should work!

---

