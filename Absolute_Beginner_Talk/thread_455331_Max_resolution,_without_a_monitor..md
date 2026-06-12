---
title: "Max resolution, without a monitor."
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Fleury on 2007-05-26
When no monitor is connected to my Ubuntu-Desktop (latest version) machine, it seems to lock the max resolution to either 640x480 or 800x600 (I cannot remember which), yet with a monitor connected, I can go to my LCD Monitor's native resolution of 1280x1024. Considering I connect to this machine via remote-desktop only, I don't have a spare monitor to keep connected to it.

Is there a way to forcibly set the resolution ?

---

### Post by raeb on 2007-05-26
You could try editing your xorg.conf to only have one resolution.  In the 'Screen' Section, for each subsection edit the resolutions so only 1280x1024 is there.  (Always remember to backup your xorg.conf file before you do this incase somethin goes haywire, cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup)

---

