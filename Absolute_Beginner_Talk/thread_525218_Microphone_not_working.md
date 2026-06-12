---
title: "Microphone not working?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by hanuman1000 on 2007-08-14
When i use Skype my mic does not capture what I say?

In Alsamixer (1.0.13) i go with tab to Capture, but i cant raise the volume (it is zero) on "Mic" and the text (L   R and CAPTUR) is red? 

when i run amixer i get this:

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 61 [97%] [on]
  Front Right: Playback 61 [97%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 12 [80%] [18.00dB] [on]
  Front Right: Capture 12 [80%] [18.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Docking-Station',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

can anyone help me please?

---

### Post by Hospadar on 2007-08-14
You might try the graphical mixer, double click the volume control in the system tray, go to edit->preferences and add all the other choices, and then go to recording and unmute the mics and turn them up.

Also in options you can edit your input source.

---

