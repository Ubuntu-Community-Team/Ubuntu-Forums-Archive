---
title: "bluetooth-alsa (a2dp driver) problems"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by frojnd on 2007-05-26
So this is the thing. I was trying to install bluetooth-alsa by this tutorial: [http://bluetooth-alsa.sourceforge.net/build.html](http://bluetooth-alsa.sourceforge.net/build.html) when I came to the point that I don't know any further. I can't find any alsa-plugins/sample.a2dprc or a2dprc.
Maybe Is some other way to install or edit this driver configuration?

---

### Post by frojnd on 2007-05-28
anyone ??

---

### Post by frojnd on 2007-05-31
anyone???

---

### Post by lodp on 2007-06-28
the line should be..

```
cp alsa-plugins**/a2dpd**/sample.a2dprc ~./a2dprc
```

so the sample file that you copy to your home dir is  not in /plugz/alsa-plugins but in /plugz/alsa-plugins/a2dpd

EDIT: Actually, that line is already fixed the line in their online documentation.

---

### Post by wieman01 on 2007-06-28
Does this help provide any insight?

[http://ubuntuforums.org/showthread.php?t=486087]("http://ubuntuforums.org/showthread.php?t=486087")

We could continue the discussion from there. I could get my Plantronics 590 finally working with Skype, etc. Took me a while to figure it out though... (Kubuntu Feisty).

---

