---
title: "asus K70IJ Intel HDA VT1708S audio crackling Ubuntu 12.04 LTS"
date: 2014-03-02
forum: Asus Ubuntu Support (CLOSED)
---

### Post by JIdC on 2014-03-02
I have tried changes to options snd-hda-intel in /etc/modprobe.d/alsa-base.conf to no avail.  

In particular, I've tried:
options snd-hda-intel position_fix=2
options snd-hda-intel position_fix=1

and then, when it did not work, I've also tried:
options snd-hda-intel enable_msi=1

I have also looked up the model for the same file to no avail, as in: options snd-hda-intel model=auto


The sound keeps on crackling (sub&#347;econd cracks, which is very annoying) with VLC, Quodlibet, etc. So, it's not an application bug. 

Can someone please guide me to sort out this problem?

---

