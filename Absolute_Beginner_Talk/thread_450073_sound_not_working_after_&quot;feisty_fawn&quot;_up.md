---
title: "sound not working after &quot;feisty fawn&quot; update"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by bradmayne on 2007-05-20
Hey whats up! I'm new to ubuntu but not linux. I was running fedora core 6 before switching to ubuntu.  Besides having a few problems getting my wireless up and running everything's cool!  however, now since the "feisty fawn" update i am not hearing any of the "music" during boot!! Can   
anyone give me a hand on this one?  P.S. I'm  working with a toshiba satellite a135 s4529 intel dual core with 1 gig of ram.

---

### Post by jiminycricket on 2007-05-21
Type these into the terminal and post the info here:

```
lspci -v | grep sound
```
```
aplay -l
```

Do you hear any sound if you test in System->Preferences->Sound ?

Some links
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Troubleshooting#How_to_configure_sound_to_work_properly_in_GNOME](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Troubleshooting#How_to_configure_sound_to_work_properly_in_GNOME)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Toshiba soundcards supported in ALSA: [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Toshiba#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Toshiba#matrix)

---

### Post by hamidaddin on 2007-05-21
I am using a Toshiba Satellite A100 and had a similar problem after upgrade. Adding the following line at the end of /etc/modprobe.d/alsa-base  resolved my problem:

```
options snd-hda-intel model=3stack
```


Solution found in: [http://baheyeldin.com/technology/linux/ubuntu-edgy-6-10-to-feisty-7-04-upgrade-sound-and-video-issues.html](http://baheyeldin.com/technology/linux/ubuntu-edgy-6-10-to-feisty-7-04-upgrade-sound-and-video-issues.html)

---

### Post by bradmayne on 2007-05-25
The following helped!!  Adding the following line at the end of /etc/modprobe.d/alsa-base


 options snd-hda-intel model=3stack

---

### Post by sirab on 2007-05-25
how do i put the line on the end

whenever i try it says its a read only file

---

### Post by jimrz on 2007-05-26
> **sirab said:**
> how do i put the line on the end

whenever i try it says its a read only file 

from the terminal

```
sudo gedit /etc/modprobe.d/alsa-base
```

then add the line, save the file and you should be in business. you may have to restart for it to take effect.

---

### Post by sirab on 2007-05-26
It worked. Thanks so much.

---

### Post by jms1989 on 2007-09-08
It didn't work for me.

---

