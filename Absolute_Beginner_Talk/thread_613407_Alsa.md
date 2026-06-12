---
title: "Alsa?"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Codix121 on 2007-11-14
Is there any way to completly wipe off alsa,
I mean all of it?

and reinstall it.

---

### Post by Inxsible on 2007-11-14
```
sudo aptitude remove alsamixer
```should remove it, but i would be careful doing that.

what are the problems that you have? maybe they can be fixed

---

### Post by Codix121 on 2007-11-14
well i have posted numerous post on the problem
and have gotten no answers.

When i play XMMS for example or anything it says:

Failed to open audio output:
ALSA 1.2.15 Output Plugin

or something of the sort.
I've tried looking for the plugin and have gotten no look.

Originally, the sound did not work
and i did this tutorial for toshiba laptops and it worked.
then my sound quit working randomly for no apparent reason.

I tried to do the tutorial again
and then when i move my volume scroll on my laptop,
the volume icon doesnt go up nor down.

as if it has no volume.
I also ran recovery mode
and it says sound card not found.

so, i was thinking of uninstalling alsa
and reinstalling, idk if that can fix the problem...

---

### Post by init1 on 2007-11-14
Running
```

sudo alsaconf

```
might work.

---

