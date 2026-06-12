---
title: "sound has gone"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-07-31
everything was good, then all of a sudden there was no sound on my system. Nothing when I play movie, nothing when I start my system. does anyone have any guess as to what has happened?

---

### Post by be4truth on 2007-07-31
Try

```
sudo dpkg-reconfigure alsa-base

```

if this doesn't work type

```
sudo dpkg-reconfigure linux-sound-base
```

and try ALSA or OSS sound system.

Then reboot your computer.

---

