---
title: "How Do I Install GStreamer?"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by EleFlameMax on 2007-12-26
I just downloaded "PiTiVi" and find it to be very primitive. It's supposed to have an edit button and a complex view, but I don't see it. I think it's because I don't have GStreamer. I went to their website and they don't support Ubuntu. Is it available for Ubuntu and can I install it?

---

### Post by overdrank on 2007-12-26
> **EleFlameMax said:**
> I just downloaded "PiTiVi" and find it to be very primitive. It's supposed to have an edit button and a complex view, but I don't see it. I think it's because I don't have GStreamer. I went to their website and they don't support Ubuntu. Is it available for Ubuntu and can I install it?

Hi and gstreamer is in add and remove under applications.

---

### Post by LowSky on 2007-12-26
in terminal type

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by AndyCooll on 2007-12-26
> **LowSky said:**
> in terminal type

```
sudo apt-get install ubuntu-restricted-extras
```

That command is fine to a point. However, you should be aware that it also installs other "restricted" extras too (e.g. Flash plugin, Java runtime environment, Microsoft fonts etc) not just gstreamer. If you want them all then go ahead, 

However if you prefer to be a little more choosy as to what you install open up Add/Remove and do a search for gstreamer. You can then pick and choose the exact plugins that you'd like to use. You will find that you probably already have some installed just not the "restricted" ones, i.e. those for mp3 etc.

:cool:

---

