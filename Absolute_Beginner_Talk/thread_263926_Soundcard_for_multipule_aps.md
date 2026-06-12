---
title: "Soundcard for multipule aps?"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by DiJEH on 2006-09-23
Is there any way to get a soundcard to work for multipule applications at once? Right now it refuses to do anything if something else is using sound.

---

### Post by henriquemaia on 2006-09-24
Check this other thread. Probably you'll find the solution there:

[**Comprehensive Sound Problem Solutions Guide**]("http://ubuntuforums.org/showthread.php?t=205449&highlight=multiple+sounds")

---

### Post by slimdog360 on 2006-09-24
Or you could get a new sound card (just a cheap one) as most are able to let you play from more then one source.

---

### Post by DiJEH on 2006-09-24
I would but I'm not sure my power supply would like many more things leeching off it.

I can't for the life of me find the config settings the link above says is there. If I change the config in AMMX I can get the file to play but no sound comes through as opposed to not playing at all, so I suppose it's at least a step forward.

---

### Post by ubuntuuser on 2006-09-24
This problem has already been addressed in multiple Howto-threads. Please use the search function before posting.

[Look here.]("http://ubuntuforums.org/showthread.php?t=32063") That's just one example.

---

### Post by DiJEH on 2006-09-24
I get that but people are assuming them tutorials are easy to use and they arn't. For example it says "insert the following" and then doesn't say if you need to save it or not.. Terminal doesn't give you hints you know.

edit. I tried the tutorial and now I have no sound at all.

stephen@Stephen:~$ sudo apt-get install libesd-alsa0
Reading package lists... Done
Building dependency tree... Done
libesd-alsa0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
stephen@Stephen:~$ sudo gedit /etc/asound.conf
- using device default
- using device default
ALSA lib conf.c:1592:(snd_config_load1) _toplevel_:1:1:Unexpected char
ALSA lib conf.c:2837:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2700:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3066:(snd_config_update_r) hooks failed, removing configuration

---

### Post by ubuntuuser on 2006-09-24
> **DiJEH said:**
> I get that but people are assuming them tutorials are easy to use and they arn't. For example it says "insert the following" and then doesn't say if you need to save it or not.
No offense intended, but common sense should tell you that you have to save the changes to the files.

That error tells you that there is an unexpected character in the /etc/asound.conf file. Typo?

Does it work again when you revert the changes, i.e. use your backup of asound.conf?

---

### Post by DiJEH on 2006-09-24
As I just pointed out I'm a newbie to Linux. I dont know how to revert to my back up.. seeing a problem?

Also how do you typo a copy and paste?

---

