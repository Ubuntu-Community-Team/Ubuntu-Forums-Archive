---
title: "No sound on ASUS B53S"
date: 2012-03-26
forum: Asus Ubuntu Support (CLOSED)
---

### Post by cslashm on 2012-03-26
Hi all,

I have recently buy a ASUS B53S and did not success in making the sound card works :(
I tried various options for snd-hda-intel module (model, position_fix, id, index...) according to info retrieved from google and alsa project...
For each try, I also play with the mixer...
But no way, there is still no sound.

If anybody can help me, it would be very nice
the alsa-info of my laptop is here

 [http://www.alsa-project.org/db/?f=3b1df59112288f5d6ec0176416fc3e1876528eb9](http://www.alsa-project.org/db/?f=3b1df59112288f5d6ec0176416fc3e1876528eb9)

Thanks


C/M.

---

### Post by mörgæs on 2012-03-27
For problems with sound, this thread is a better option:
[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

---

### Post by lovinglinux on 2012-03-31
Try this:

open /etc/modprobe.d/alsa-base.conf with a text editor:

```
gksudo /etc/modprobe.d/alsa-base.conf
```

Add the following line:

```
options snd-hda-intel probe_mask=1 model=asus-v1s
```

Save and reboot.

It worked for my new ASUS A43E

BTW, sound wasn't working on Unity but was working with Gnome Shell.

---

