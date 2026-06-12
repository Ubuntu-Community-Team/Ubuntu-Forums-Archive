---
title: "/dev/snd/controlC0 missing"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by RayDeCampo on 2008-02-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/185811](https://bugs.launchpad.net/bugs/185811) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello,

I am a new Ubuntu user struggling to get sound working on my system.  I am using onboard sound with a M2N-E SLI motherboard; it uses USB Audio.  After install there was no /dev/sbd/controlC0 node although there was a /dev/snd/controlC1 node:

$ ls -l /dev/snd
total 0
crw-rw---- 1 root audio 116, 6 2008-01-22 20:59 controlC1
crw-rw---- 1 root audio 116, 5 2008-01-22 20:59 pcmC1D0c
crw-rw---- 1 root audio 116, 4 2008-01-22 20:59 pcmC1D0p
crw-rw---- 1 root audio 116, 3 2008-01-22 20:59 seq
crw-rw---- 1 root audio 116, 2 2008-01-22 20:59 timer

I have attached the other usual outputs to the referenced bug report.  After manually configuring Preferences->Sound to use USB Audio some applications work with sound but others do not.  E.g., mpg321 fails:

ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
No default libao driver available.

I'd appreciate any help.

Thanks,
Ray

---

### Post by RayDeCampo on 2008-02-02
Wow, an hour and this topic is already on page three...

---

