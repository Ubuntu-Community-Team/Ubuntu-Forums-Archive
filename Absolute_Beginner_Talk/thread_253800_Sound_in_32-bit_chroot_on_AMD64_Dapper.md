---
title: "Sound in 32-bit chroot on AMD64 Dapper"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by mewray on 2006-09-08
I've successfully followed the HOWTO on installing 32-bit apps in a chroot jail on 64-bit Ubuntu, but my sound isn't working on the 32-bit apps.  I keep getting a couple errors:

```
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
```

I also get this problem when running synaptic32:
```
(synaptic32:16741): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
```

I've installed the ubuntu-desktop package, and so theoretically have all the necessary files for a gnome graphical desktop inside the chroot.  Anyone know what I can do to fix the Gtk-WARNING... or more importantly, what I can do to get sound on my 32-bit programs?  I can't seem to find this information anywhere!

---

