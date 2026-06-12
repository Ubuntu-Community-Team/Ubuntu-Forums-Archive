---
title: "ALSA Reinstallation"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by falk3r on 2007-03-27
I'm trying to use these directions:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Nvidia&card=.&chip=nForce&module=intel8x0#opt](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Nvidia&card=.&chip=nForce&module=intel8x0#opt)

To re-enable ALSA audio... and I'm as far as knowing that I do not have this soundcore module on my machine.

```
falk3r@falk3r-desktop:~$ modinfo soundcore
modinfo: could not find module soundcore
```

In newb-ian terms, how do I go about reinstalling this module?

 - falk3r

---

### Post by Mark_in_Hollywood on 2007-03-27
I'm as newb as thou, but I can suggest:

[http://www.ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

do be very careful about the

 VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following

portion. I didn't know about it until too late. The system ate my desktop and I had to reinstall the entire system. Lost my /home and everything.

If while installing

sudo apt-get install linux-sound-base alsa-base alsa-utils

you see that apt-get has removed ANYTHING, reinstall it before re-booting your computer or turning off the computer. PERIOD.

---

### Post by falk3r on 2007-03-27
Check, packages reinstalled... any idea about this message?

```
alsamixer: relocation error: alsamixer: symbol snd_mixer_selem_get_playback_dB, version ALSA_0.9 not defined in file libasound.so.2 with link time reference
```

When I run "alsamixer"

 - falk3r

---

### Post by Mark_in_Hollywood on 2007-03-29
Sorry, that way way way too beyond me.

---

### Post by falk3r on 2007-03-29
That's alright, a good old reformat + fresh install of Ubuntu 6.10 did the trick.

---

### Post by click4851 on 2007-03-29
Its might be too late at this point, but I was facing such a dilema recently and decided to create a sperate home partition. Makes for a much easier clean install

---

