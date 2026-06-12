---
title: "startup log file ?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by megadyptes on 2006-09-19
This is one of those easy questions that I just can;t find the answer to.. When my system is going through its startup, and all the variious services etc are scrolling past, one of them is listed has having failed but it goes passed too quick for me to read which one it is. Surely, these are being logged somewhere, but where?

 Thanks

---

### Post by Jussi Kukkonen on 2006-09-19
```
dmesg
```
Hope this helps.

---

### Post by megadyptes on 2006-09-19
Hmmm, well that certainly lists a whole load of things I doubt I'll ever understand!:)

I was hoping that there was an easy way of finding out what the messages in the screenshot below were, and whether they were marked as ok or *failed.* The screenshot isn't from my PC, it's just an example of the bit I was hoping was logged somewhere.[I]

[IMG]http://oculusaquilae.de/kubuntu/breezy-neu/images/usplash.png[/IMG]
[/I]

---

### Post by Jussi Kukkonen on 2006-09-20
Ahh, I see. I don't think that's saved anywhere -- the contents should be just a "sanitized" version of dmesg output...

I suggest wading through dmesg output. If you can't find the problem, paste the output (or maybe just some suspicious lines) here.

---

