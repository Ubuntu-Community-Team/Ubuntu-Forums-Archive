---
title: "Problems with MacBookAir 3,1 and Cirrus Logic"
date: 2011-07-08
forum: Apple Hardware Users
---

### Post by meelthon on 2011-07-08
Hello

I am running Ubuntu 10.04 LTS on a 3rd gen MacBookAir 3,1.  I successfully installed the OS thanks to the Ubuntu forum help.  However, although I've tried many times to configure sound properties, I still have no sound from the speakers.

-I have run alsamixer and confirmed that it is not muted.
-I have edited in /etc/modprobe.d/alsa-base.conf and added the following with no luck: options snd-hda-intel model=mba31

I found that for the Cirrus Logic CS4206 (which is the biult-in sound card) the mba31 is not working on my machine, but when I change it to either "mbp55", "imac27", or "auto", and run sudo alsa force-reload, the speakers suddenly start to work.  If I restart I lose sound through the speakers.

How could I fix this issue?

---

