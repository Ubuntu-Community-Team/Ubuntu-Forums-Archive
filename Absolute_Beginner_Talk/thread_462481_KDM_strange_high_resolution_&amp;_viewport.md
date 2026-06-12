---
title: "KDM strange high resolution &amp; viewport"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Songwind on 2007-06-02
My computer started showing me KDM with a really high resolution, but keeping a viewport the same size as my default resolution setting.

It's in widescreen.

So, KDM is displaying at something like 1900X1200 resolution, but only showing me 1680X1050 of it at a time.  This is very frustrating, particularly since I don't recall ever setting it that way.

I went through the KDM documentation and can't find anywhere that it's configured like that.  I also removed all references in my xorg.conf to 1900X1200, since I am not planning to ever use that resolution.

Any ideas?

Eric

---

### Post by Clay_Banger on 2007-06-04
i think there is a problem with your xorg.conf
```
kdesu kate /etc/X11/xorg.conf
```
then browse through till you get to a section that looks like this:
```
Section "Screen"
  Identifier "Default Screen"
  Device "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    **virtual 1280 1024**
    modes "1280x1024@75"
  EndSubSection
EndSection
```
change the 'virtual' bit to the resolution that you normally use.

so
```
virtual 1900 1200
```
becomes
```
virtual 1680 1050
```

---

### Post by Songwind on 2007-06-04
Holy oversight, Batman!

I had visually scanned xorg.conf once already looking for that setting and missed it.  Apparently, grep is our friend.

Fixed, thanks for prompting me to look again.

---

### Post by Clay_Banger on 2007-06-05
> **Songwind said:**
> Holy oversight, Batman!

I had visually scanned xorg.conf once already looking for that setting and missed it.  Apparently, grep is our friend.

Fixed, thanks for prompting me to look again.
No problem, i'm glad it worked out for you.

---

