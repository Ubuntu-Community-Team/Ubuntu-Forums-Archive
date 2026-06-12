---
title: "x86-64 blues"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by vorbalhorde on 2007-10-19
Hello everyone.  I have an Intel Core2Duo E6700 processor, so downloaded and installed the 64-bit version of Gutsy Gibbon.  I also have a Creative X-Fi sound card.  I recently discovered that my sound card is not supported, so I set off to find drivers.  Once I downloaded the drivers and extracted the archive I went to install, but ran into this error.

```
This product only support 64-bit Operating Systems
Setup will now exit
```

But Adobe's Flash player says that I DO have the 64-bit version.

```
ERROR: your architecture, \'x86_64\', is not supported by the Adobe Flash Player installer.
```

What gives?

---

### Post by Linux_Man on 2007-10-19
Adobe doesn't have a x86-64 version of Flash out yet. The best thing you can do right now is either to reinstall using the x86 32-bit version (Your hardware will be just as supported even though you have a 64 bit processor) or use GNASH (A free flash player that is about equivalent to Flash 7)

---

### Post by Paul820 on 2007-10-19
Flash is in the repositories for 64bit, i'm using it. From the teminal:
> sudo apt-get install flashplugin-nonfree

---

### Post by vorbalhorde on 2007-10-19
Thanks for the flash tips, that's a big help.  Any clues about the sound card drivers installer error?  Why does it say that I don't have the 64-bit version of Gutsy?

---

### Post by rsambuca on 2007-10-19
> **Linux_Man said:**
> Adobe doesn't have a x86-64 version of Flash out yet. The best thing you can do right now is either to reinstall using the x86 32-bit version (Your hardware will be just as supported even though you have a 64 bit processor) or use GNASH (A free flash player that is about equivalent to Flash 7)

WRONG.  It is in the Gutsy repos now.

---

### Post by vorbalhorde on 2007-10-19
Sad thing is the Feisty Fawn distro didn't support my motherboard's LAN capabilities, and now my sound card isn't supported.

---

