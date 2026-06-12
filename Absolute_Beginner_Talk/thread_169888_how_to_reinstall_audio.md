---
title: "how to reinstall audio"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by chrluc on 2006-05-03
hay guys, i tried to reconfigure my audio to allow skype to work and it messed everything up. Now audio does not work at all. Is there a way to "reinstall" just the audio to back to original configuration.

thanks

---

### Post by ComplexNumber on 2006-05-03
reinstallation may not be necessary. what do you mean by "it doesn't work"? i mean, in what way? whats 'signs' do you have that it doesn't work?

---

### Post by chrluc on 2006-05-03
there is no audio, were as before there was, on everything. audio was not a problem till i fallowed some guides on getting skype to work. tried tro change the output in multimedia system selector and it did not help. as part of the guide i rewrote several audio.conf files.

---

### Post by ComplexNumber on 2006-05-03
> as part of the guide i rewrote several audio.conf files. i don't suppose you kept a backup copy.

it may well be that the audio device was changed in the process. go to command line (if its not in the menu) and type gnome-volume-control. then go to 'File' on the main menu and select 'change device'. try changing the device and then playing some audio. also have alook around that same application and see if the volume is not muted or turned down.
you can also try the multimedia properties in the menu (if its not there, type gstreamer-properties on the command line) and see if there is anything 'wrong' there.

---

### Post by chrluc on 2006-05-03
well actually i made a backup of on of the .conf file and tried to rewrite it and had no sucess with the audio comming back. gstreamer-properties gave these results 
ALSA lib conf.c:1578:(snd_config_load1) _toplevel_:45:1:Unexpected char
ALSA lib conf.c:2823:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2686:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3052:(snd_config_update_r) hooks failed, removing configuration

---

### Post by ComplexNumber on 2006-05-03
[quote=chrluc]well actually i made a backup of on of the .conf file and tried to rewrite it and had no sucess with the audio comming back. gstreamer-properties gave these results 
ALSA lib conf.c:1578:(snd_config_load1) _toplevel_:45:1:Unexpected char
ALSA lib conf.c:2823:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2686:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3052:(snd_config_update_r) hooks failed, removing configuration[/quote]
that output looks rather odd. it should just bring up the multimedia selector GUI thats in the menu :confused:. what happens when you type gnome-volume-control on the commandline?

---

### Post by chrluc on 2006-05-03
the same error in terminal as with gstreamer-properties, but they both bring up the gui control but again with the error in terminal. is there a way to just reconfigure the audio from scratch or does that require a complete reinstall?

---

