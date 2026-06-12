---
title: "Some ALSA bug?"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by darkchron on 2006-11-29
Hey ubuntu users, i got this problem i wan't to share with you.

This keep comming up when i am done editing my xorg.conf or whatever, i can't figure out why it keep comming up..

Look at this, i just edited my xorg.conf and this error was pasted to my terminal.

```
darkchron@chronicbase:~$ sudo gedit /etc/X11/xorg.conf
Password:
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:nForce2
```

I did nothing to alsa configuration, it shows me that everytime i am done editing something with gedit.

thx in advance:KS

---

### Post by darkchron on 2006-11-30
FIXED by reinstalling alsa ;)

---

### Post by cartel on 2006-12-02
How exactly did you reinstall ALSA? I am having this problem too, so it's not just you.

---

### Post by pakux on 2006-12-03
I've just found something in another thread that may give you an idea:

[http://ubuntuforums.org/showpost.php?p=1763628&postcount=24](http://ubuntuforums.org/showpost.php?p=1763628&postcount=24)

hope it helps.

---

