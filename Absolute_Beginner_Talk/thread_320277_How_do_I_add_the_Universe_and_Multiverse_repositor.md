---
title: "How do I add the Universe and Multiverse repositories? [Resolved]"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by DesertFox69 on 2006-12-17
Hello,

Im new to Ubuntu and I was just reading help on how to add the Universe and Multiverse repositories.  It states that "Open System->Administration->Software Properties" but I dont see a "Software Properties" in my administration menu.  I see a software sources, but not a software properties.  Am I missing something here?  Im using 6.10.

Thanks in advance!

---

### Post by scrooge_74 on 2006-12-17
Look in the system administration for Synaptic there you can enable the other repositories

or from a command terminal you can do sudo nano /etc/apt/sources.list and uncomment the repositories

---

### Post by aysiu on 2006-12-17
Software Sources is the same as Software Properties.

I believe Software Properties is what it was called in Dapper, but it's now Software Sources in Edgy.

If you prefer the command-line, you can do this:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by DesertFox69 on 2006-12-17
Hmm, i uncommented like the first post said, but I still cant seem to download the gstreamer-ugly package for codecs.

---

### Post by aysiu on 2006-12-17
> **DesertFox69 said:**
> Hmm, i uncommented like the first post said, but I still cant seem to download the gstreamer-ugly package for codecs.
After you save your new sources.list, you have to update the repositories list so that the package manager knows what's now available: ```
sudo aptitude update
```

---

### Post by DesertFox69 on 2006-12-21
Thanks.  Got it working.

---

