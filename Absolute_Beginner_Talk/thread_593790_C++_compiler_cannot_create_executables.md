---
title: "C++ compiler cannot create executables"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by infamous16 on 2007-10-27
I get this alot, and I tried 

sudo apt-get install g++

but it said

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How can I fix this? Using gutsy btw.

---

### Post by sad_iq on 2007-10-27
The error appears when you have an apt-get stuff working in your system and you have synaptic opened. just close synaptic. If the problem persists do a ```
sudo rm /var/lib/dpkg/lock
``` I think you also need to install build-essential: ```
sudo apt-get install build-essential
```

---

