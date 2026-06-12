---
title: "No sound"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by jezg on 2007-10-14
Hi all,

I am a complete newb to Linux & Ubuntu. I have just downloaded & installed Ubuntu 7.04 in a VMWare image on top of Windows XP on an Dell Inspiron 9300. My sound control is not working. I have looked around the forums (not being lazy :0)). I have found references to snd_pcm_oss but can not find how to install it as the Applications Add/Remove function does note recognize this as a valid package to install. When I go into the System - Preferences - Sound option, I am unable to select any Default Mixer Tracks (as suggested in one forum posting) - the list is empty. 

Please can you help ?

Thanks

Jez

---

### Post by Frak on 2007-10-14
Have you installed VMWare tools?

---

### Post by jezg on 2007-10-15
Yes, I have installed VMWare tools.

Any other suggestions welcome :-)

Jez

---

### Post by Frak on 2007-10-15
Is sound (on VMware) enabled?

Also, turn up your volume to see if its that. I've had problems with volume being too low in default VMware installations.

---

### Post by Therion on 2007-10-15
Had a very similar problem.  The **Getting the ALSA drivers from a *fresh* kernel** section of this thread:

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide")

Is what got my sound up and running smoothly.

---

