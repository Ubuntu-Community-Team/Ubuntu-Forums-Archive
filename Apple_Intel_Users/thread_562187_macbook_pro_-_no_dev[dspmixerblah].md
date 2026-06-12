---
title: "macbook pro - no /dev/[dsp|mixer|blah]"
date: 2007-09-28
forum: Apple Intel Users
---

### Post by shinepuppy on 2007-09-28
Hey Folks,
It looks like i'm having alot of the same problems with my mac. I tried installing the alsa modules from source and now my system is royally horked! I managed to get the snd-hda-intel module to load without complaints but now the system does not create /dev/dsp, /dev/mixer, or any of the other goodies it's supposed to have. Anyone have any advice? :confused:

---

### Post by cyberdork33 on 2007-09-28
> **shinepuppy said:**
> Hey Folks,
It looks like i'm having alot of the same problems with my mac. I tried installing the alsa modules from source and now my system is royally horked! I managed to get the snd-hda-intel module to load without complaints but now the system does not create /dev/dsp, /dev/mixer, or any of the other goodies it's supposed to have. Anyone have any advice? :confused:

if you are going to replace modules that are already provided in the repos, you have to block that default module from loading before your compiled module will be used instead. You configure what modules are not used in [SIZE=-1]/etc/default/linux-restricted-modules-common[/SIZE]

---

