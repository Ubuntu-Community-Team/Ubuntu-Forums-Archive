---
title: "sound issues and ALC655"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by realityintrudes on 2006-01-19
OK, been trying to get my onboard AC97 alc655 sound to work.

lspci says:

0000:00:10.2 Multimedia audio controller: nVidia Corporation: Unknown device 026b (rev a2)


running 'esd' from the terminal outputs:
ALSA lib confmisc.c:560: (snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479 :(_snd_config_evaluate) function snd_func_card_driver return ed error: No such file or directory
ALSA lib confmisc.c:392: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_concat returned er ror: No such file or directory
ALSA lib confmisc.c:955: (snd_func_refer) error evaluating name
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_refer returned err or: No such file or directory
ALSA lib conf.c:3948: (snd_config_expand) Evaluate error: No such file or directo ry
ALSA lib pcm.c:2090: (snd_pcm_open_noupdate) Unknown PCM default
steven@ubuntu:~$ alsa
bash: alsa: command not found
steven@ubuntu:~$ esd
ALSA lib confmisc.c:560: (snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_card_driver return ed error: No such file or directory
ALSA lib confmisc.c:392: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_concat returned er ror: No such file or directory
ALSA lib confmisc.c:955: (snd_func_refer) error evaluating name
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_refer returned err or: No such file or directory
ALSA lib conf.c:3948: (snd_config_expand) Evaluate error: No such file or directo ry
ALSA lib pcm.c:2090: (snd_pcm_open_noupdate) Unknown PCM default
steven@ubuntu:~$ esd
ALSA lib confmisc.c:560: (snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_concat returned error: No such file or direc tory
ALSA lib confmisc.c:955: (snd_func_refer) error evaluating name
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_refer returned error: No such file or direct ory
ALSA lib conf.c:3948: (snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090: (snd_pcm_open_noupdate) Unknown PCM default
steven@ubuntu:~$ esd
ALSA lib confmisc.c:560: (snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:955: (snd_func_refer) error evaluating name
ALSA lib conf.c:3479: (_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3948: (snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2090: (snd_pcm_open_noupdate) Unknown PCM default



Running 'alsamixer' from the terminal produces:
alsamixer: function snd_ctl_open failed for default: No such file or directory



I have downloaded the newest realtek drivers: realtek-linux-audiopack-3.5.6, and have them extracted on my desktop.  Where from here?

---

