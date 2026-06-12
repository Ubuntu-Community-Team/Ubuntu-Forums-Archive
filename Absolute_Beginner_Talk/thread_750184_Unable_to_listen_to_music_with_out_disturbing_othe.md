---
title: "Unable to listen to music with out disturbing others"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by raghu_equinox on 2008-04-09
Hi Good People,

I have been using Ubuntu since couple of months now and I really find it cool.
Whenever I play any music/video, even with my Headset/Headphones plugged into the M/C I can hear the same from the CPU speaker too...

Do we have a fix for this?

Thanks
--Raghu

---

### Post by Tomatz on 2008-04-09
Turn your speakers off?

Mute the speaker output?

---

### Post by raghu_equinox on 2008-04-09
Turing CPU speakers off!!..?
I tried to do that form the Advance Volume Control wizard ..no help

---

### Post by misfitpierce on 2008-04-09
Terminal : gnome-volume-control

maybe turn down speaker volume and keep headset turned up for now until you figure out perm fix for it.

---

### Post by eriqjaffe on 2008-04-09
You can "blacklist" the PC Speaker by adding the following line to /etc/modprobe.d/blacklist (you need to do this as root, btw):

```
blacklist pcspk
```

The next time you reboot, the speaker will be silenced.  If you ever need to re-enable the speaker...

```
sudo modprobe pcspkr
```

---

