---
title: "Thunderbird updated... now it won't stay on"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-09-26
Just this morning I installed the latest update, which involved Thunderbird using less memory, as I recall. Now I launch T-bird, it loads, it starts checking for new mail, and then disappears. It certainly does use less memory this way, but I doubt this is what was intended. Anyone else have this issue?
TIA

---

### Post by whizbaby on 2006-09-26
Start it from terminal
**mozilla-thunderbird**
and post the error message(s).

---

### Post by ricardisimo on 2006-09-26
> **whizbaby said:**
> Start it from terminal
**mozilla-thunderbird**
and post the error message(s).

Here's everything:
```
DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1
** (Gecko:10672): CRITICAL **: eazel_engine_image_render: assertion `width > 0' failed
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131: 10672 Segmentation fault      "$prog" ${1+"$@"}

```

Thanks again.

---

### Post by Bigbluecat on 2006-09-26
Try starting it in safe mode. I saw this thread regarding problems with Thunderbird themes. I don't know if this is your problem but safe mode may at least help you get Tbird flying again.

[http://www.ubuntuforums.org/showthread.php?t=263085&highlight=thunderbird+safe](http://www.ubuntuforums.org/showthread.php?t=263085&highlight=thunderbird+safe)

---

### Post by veraction on 2006-11-19
I discovered that the problem was with the Crux theme. After switching, it works fine for me.

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=29795](https://bugs.eclipse.org/bugs/show_bug.cgi?id=29795)

---

### Post by ricardisimo on 2006-11-30
> **veraction said:**
> I discovered that the problem was with the Crux theme. After switching, it works fine for me.

[https://bugs.eclipse.org/bugs/show_bug.cgi?id=29795](https://bugs.eclipse.org/bugs/show_bug.cgi?id=29795)

I'm trying to be better about closing out my threads. I switched themes, and that seems to have done it. Thanks for the tip. Odd that the theme would cause that problem. Nice looking theme, too... shame.

---

