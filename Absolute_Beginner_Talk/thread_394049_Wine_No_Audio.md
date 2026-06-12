---
title: "Wine No Audio"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by falk3r on 2007-03-26
World of Warcraft has no audio/sound of any kind. Loading via Wine with the following Audio options set:

```
winecfg
```

OSS Driver Checked (nothing else)
Hardware Acceleration: Emulation
Default Sample Rate: 22050
Defaults Bits Per Sample: 8
Driver Emulation (tried with this checked and unchecked)

I have installed libjack-0.100.0-0 via synaptic, ran the following code:

```
sudo cp /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so
```

and ran some more code to help with an "ALSA issue".

```
sudo modprobe snd-seq
```

As a side note, in VLC audio works fine. Any advice?

Thank you for your time,
- falk3r

---

### Post by Madmoose on 2007-03-30
The only game I get sound with is Starcraft, but all my others don't. I would like to know the fix as well.

---

### Post by mmendez on 2007-05-25
Check this link out that deals with the same issue

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=449251&highlight=no+audio+in+starcraft[/COLOR]]("http://ubuntuforums.org/showthread.php?t=449251&highlight=no+audio+in+starcraft")

> **knn said:**
> Those are just warnings, they're normal. You don't need the jack library, just use alsa as the audio output. The other two are missing features, but I don't think Starcraft needs sound capture. In fact, Starcraft should work pretty well with Wine:
[wine appdb entry]("http://appdb.winehq.org/appview.php?iVersionId=149&iTestingId=11607")

I was getting no sound at all and when I deselected OSS and selected ALSA everything was working A OK so you might want to try this

---

### Post by Enverex on 2007-05-25
> **mmendez said:**
> Check this link out that deals with the same issue

[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=449251&highlight=no+audio+in+starcraft[/COLOR]]("http://ubuntuforums.org/showthread.php?t=449251&highlight=no+audio+in+starcraft")



I was getting no sound at all and when I deselected OSS and selected ALSA everything was working A OK so you might want to try this

That quote is wrong. OSS is the only stable and fully featured (well, more than the others) driver at the moment, all the others have lots of bugs and general issues. If you're not getting sound from Wine using the OSS driver then follow this:

[http://wiki.winehq.org/FAQ#head-ae1ede4cf67a9cea369a131b0087129dbb70e322](http://wiki.winehq.org/FAQ#head-ae1ede4cf67a9cea369a131b0087129dbb70e322)

---

