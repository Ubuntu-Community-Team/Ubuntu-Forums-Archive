---
title: "Problem with playing fullscreen video"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by mrblondeisback on 2007-10-02
I'm new to Ubuntu and Linux in general, and I have been nothing but impressed except for one fairly large issue.  I tried to watch a video in full screen today, and the playback was choppy, very bad, and the sound wasn't synced up.  I tried dropping resolution down to 640x480, and that fixes the problem for the most part, still a little rough but not enough to really complain about.  Is there a fix for this?  Or at least maybe a way to force 640x480 when full screen then come back automatically?  I've got an onboard graphics chipset, Intel 945G.  Do I need a new driver?  Any help would be awesome.

---

### Post by taurus on 2007-10-02
What video driver do you use in /etc/X11/xorg.conf?

Applications -> Accessories -> Terminal
```
cat /etc/X11/xorg.conf
```
What media play do you use to play your movies?

---

### Post by mysticmatrix on 2007-10-02
Are you using Desktop Effects? If yes try turning them off during videos

---

### Post by mrblondeisback on 2007-10-02
I've got the desktop effects turned off, and I'm using Totem.  I'm not at my compy now but when I get home I'll look at that conf file.  I haven't done anything more than install Ubuntu and let it set everything up for me.

---

### Post by t0n1 on 2007-10-05
Any update on the problem?

---

