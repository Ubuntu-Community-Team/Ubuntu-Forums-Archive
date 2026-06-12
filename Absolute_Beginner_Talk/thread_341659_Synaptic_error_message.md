---
title: "Synaptic error message"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by 1fastredsc on 2007-01-18
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

I tried to install some packages with synaptic but got that error message. What does it mean?

---

### Post by taurus on 2007-01-18
Run this from a command line (terminal) and paste the output here.

Applications -> Accessories -> Terminal
```
sudo aptitude update
```

---

### Post by randomnumber on 2007-01-18
sound like you have a update utility working at the same time that you are running the synaptic. Anyway you can only use one at a time (terminal apt-get, update manger, synaptic)

---

