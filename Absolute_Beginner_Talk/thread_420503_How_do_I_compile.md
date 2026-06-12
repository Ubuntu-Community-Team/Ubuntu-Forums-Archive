---
title: "How do I compile?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Happy_Man on 2007-04-23
As the title says...what do I need to compile stuff?

---

### Post by taurus on 2007-04-23
You need build-essential and checkinstall (optional).

```
sudo aptitude update
sudo aptitude install build-essential checkinstall
```

---

### Post by Perfect Storm on 2007-04-23
It really depend which format the source was made in/with. But the most used one what taurus showed to get the basic compiling tools.

In most cases, you unpack the tar.gz or tar.bz2 and cd in to the folder. There after ./configure (might be a good idea to run ./configure --help first, if you want to enable/disable change stuff etc.). If it's a libs you want to compile it's a good idea to run prefix to your /usr folder, sometimes other applications/libs can't find it if you installed it other places (rare cases nowadays). Check the output when running the ./configure it'll tell you what you're missing and/or how you are setting some of the options. As long it doesn't show Error output you can continue to next step.

**make**, sometimes the config files need a tweak/hack if errors shows up. Mostly because of a bug or a missing headers/-devs or libs.

**sudo checkinstall**, not recommenable as it's a bit unstable and my experience is that it only works %50 of the time. If it doesn't work use **sudo make install** (if required).

---

