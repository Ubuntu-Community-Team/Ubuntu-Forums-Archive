---
title: "Kernel Sources and Ubuntu Alternate CD"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by JPMaximilian on 2006-09-11
If I used the Ubuntu Alternate CD, does that mean that the kernel sources were not installed?  Also, I have to put the cd in to install certain packages with synaptic, why is that?  Thanks.

---

### Post by skymt on 2006-09-12
No Ubuntu installers install the kernel sources (to my knowledge, I haven't used them all).

For the CD issue, open Synaptic and go to Settings > Repositories, and remove any CD entries in the list.

---

### Post by bodhi.zazen on 2006-09-12
> **JPMaximilian said:**
> If I used the Ubuntu Alternate CD, does that mean that the kernel sources were not installed?  Also, I have to put the cd in to install certain packages with synaptic, why is that?  Thanks.

By default Ubuntu the kernel sources are not installed regardles of install method. strange but true. Install via synaptic.

If you are going to compile use build-essential:
```
aptitude install build-essential
```. 8)

---

### Post by JPMaximilian on 2006-09-12
I'm not trying to compile the kernel, I just need the sources in order to install some alsa drivers.

---

### Post by Najand on 2006-09-12
sudo apt-get install linux-headers-$(uname -r)

---

