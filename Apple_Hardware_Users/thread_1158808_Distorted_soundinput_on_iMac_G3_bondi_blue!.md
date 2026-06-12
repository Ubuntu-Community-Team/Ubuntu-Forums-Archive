---
title: "Distorted sound/input on iMac G3 bondi blue!"
date: 2009-05-14
forum: Apple Hardware Users
---

### Post by Cyanaether22 on 2009-05-14
Hey, I installed Xubuntu on my old iMac G3 350 MHz Power PC slot-loading bondi blue model. The main purpose of this being to set this computer as a recording device.

But.. the sound input AND output (speakers, sound in jack, sound out jack) are all distorted - not terribly, but not clean at all. this won't do for recording and listening to music isn't as enjoyable.

Since it's both input and output - and in the headphone jack output too, I'm thinking it's a sound card issue, lack of config perhaps.

I ran a few commands and here's what I got so far:

```

teagankelk@kelkimac:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
0000:00:10.0 Display controller: ATI Technologies Inc Rage 128 RL/VR AGP
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 02)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth Internal PCI
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM)

```

```

teagankelk@kelkimac:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Screamer [PowerMac Screamer], device 0: PMac Screamer [PowerMac Screamer]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

teagankelk@kelkimac:~$ cat /proc/asound/cards
 0 [Screamer       ]: PMac Screamer - PowerMac Screamer
                      PowerMac Screamer Rev 0

```

The distortion seems to minimize when i turn everything's volume down and use an external source to amplify it... so that's why everything's turned down in the following config to 0. **NOTE THAT FOR SOME REASON, 0 is not mute. this applies to the capture and playback channels. both of them are still getting fair volumes at 0, both distorted slightly.**

possibly related to this bug report - [https://bugs.launchpad.net/alsa-utils/+bug/16454](https://bugs.launchpad.net/alsa-utils/+bug/16454)

```

teagankelk@kelkimac:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Front Left - Front Right
  Capture channels: Mono
  Limits: Playback 0 - 15
  Mono: Capture [off]
  Front Left: Playback 0 [0%] [on]
  Front Right: Playback 0 [0%] [on]
Simple mixer control 'Headphone Detection',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Line',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'CD',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 2
  Mono: 0 [0%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 15
  Mono:
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%]
  Front Right: Capture 0 [0%]
Simple mixer control 'Auto Mute',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 20 [20%]

```

```

teagankelk@kelkimac:/proc/asound$ cat modules
 0 snd_powermac

teagankelk@kelkimac:/proc/asound$ cat modules
 0 snd_powermac

teagankelk@kelkimac:/proc/asound$ cat modules
 0 snd_powermac

```

I wonder if it's also reltaed to this bug topic - [https://lists.ubuntu.com/archives/ubuntu-users/2005-September/049161.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-September/049161.html) .

PLEASE HELP. I'm considering switching back to mac os. the sound is the most important thing about this computer, it's meant for recording.

---

### Post by cdenley on 2009-05-14
How is this security related? Are you sure it is a software problem and not a hardware problem?

---

### Post by Cyanaether22 on 2009-05-14
Hah whoops! I must've looked at security real quick and saw software.

could some awesome person give this a move? thanks :)

I think if anything, it's a software problem. I THINK the sound worked fine when I was running OS 9. I can't really check though, because to boot into OS 9 you need a mac os partition with os9 already on it... or something like that.

---

