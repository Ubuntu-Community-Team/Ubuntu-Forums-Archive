---
title: "Video card driver question"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by boondongle on 2007-09-26
Hi all. I'm very new to Ubuntu, and I'm having some issues. Most are things I think I can figure out on my own, given enough time and experimentation. But there's one thing that's causing me problems, and I can't find the answer to it online.

After installing Wine, I get the following message when I attempt to verify the install using winecfg:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  12
  Current serial number in output stream:  13
```

From what I can find online, this is caused by a driver problem...specifically, that I need GLX support for my video card. That's all well and good, but here's the issue...where can I find the correct drivers for my card? I tried looking online, and I thought I found the right ones, but after installing them, I get this message when I run glxgears:

```
Error: couldn't get an RGB, Double-buffered visual

```

Can anyone either point me to a very simple location where I can track down the correct drivers for my video card? It's a Visiontek x1550. Any help at all would be appreciated.

---

### Post by kellemes on 2007-09-26
Will [this thread]("http://ubuntuforums.org/showthread.php?t=554807&highlight=x1550") help?

---

### Post by boondongle on 2007-09-26
I looked through that thread and the others referenced in it, but didn't find anything to help.

I'm starting to think part of the problem is that ATI doesn't seem to support the x1550 for Linux...at least they don't have a driver for it on their website.

---

