---
title: "Totem Plugins"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Prof.Arronax on 2007-03-04
Greetings all.

What plug-in is required for Totem to be able to play .MP3 files?  I do not see an option in the program config screens to add anything.

TIA.

---

### Post by 23meg on 2007-03-04
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

---

### Post by RomeReactor on 2007-03-04
Hi. For Totem-Xine:

```
sudo apt-get install libxine1 libxine-extracodecs
```

For Totem-Gstreamer:

```
sudo apt-get install gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-ugly
```

though i'm not sure you really need **gstreamer0.10-plugins-ugly**.

---

### Post by Prof.Arronax on 2007-03-04
> **23meg said:**
> [https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

Thanks, but that link refers to the "Amarok" player which will not run on my Ubuntu 6.10.  It apparently requires the Kmail program for some odd reason.  Without it, it just puts up an error screen, times out and becomes  non-responsive requiring a forced closure by the system.

Odd that such a common format as MP3 would be considered a "restricted" format, don't you think?  Surely there must be an easier way with some program that doesn't require all the extra hoopla to get it running.

---

### Post by j.miller565 on 2007-03-04
Amarok player WILL run on Ubuntu 6.10. I used it when I was using Ubuntu and I still use it since my using Kubuntu now.

---

### Post by old_geekster on 2007-03-05
> **Prof.Arronax said:**
> Thanks, but that link refers to the "Amarok" player which will not run on my Ubuntu 6.10.  It apparently requires the Kmail program for some odd reason.  Without it, it just puts up an error screen, times out and becomes  non-responsive requiring a forced closure by the system.

Odd that such a common format as MP3 would be considered a "restricted" format, don't you think?  Surely there must be an easier way with some program that doesn't require all the extra hoopla to get it running.
What do you think this is --- Windows?:) 

Ubuntu/Linux is like getting a house from "Habitat for Humanities".  You get it for FREE, but you have to put in some sweat equity.  In other words, you have do a bit of extra work to get things the way you want it.  When you get done, it is worth the effort and you truly feel some satisfaction.

Why is such a common format in the "restricted" repositories?  It has to do with licenses and other restrictions.  Therefore, the developers of U can't include it.

Amarok will run in Ubuntu.  I have used it, but I actually like "Banshee Music Player" better.  I like listening to Pod-casts and it is setup to run them.

---

