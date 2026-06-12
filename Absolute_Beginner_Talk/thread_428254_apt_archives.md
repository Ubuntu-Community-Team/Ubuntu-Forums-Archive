---
title: "apt archives"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by ggaaron on 2007-04-30
I have a question - do every program I install get into /var/cache/apt/archives/? And does it stay there forever, or ubuntu automatically flushes archives?

Thanks in advance.
Aaron

---

### Post by Najand on 2007-04-30
It will clears out the local repository of retrieved package files if you use the ```
$ sudo apt-get clean
```. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/.

---

