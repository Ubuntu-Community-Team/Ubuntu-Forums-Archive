---
title: "No sound on internal speakers - iMac 27 +Maverick"
date: 2010-11-09
forum: Apple Hardware Users
---

### Post by c@ssie on 2010-11-09
I installed Maverick on my 27 inch iMac (core2 Duo 3 Ghz).   I weas able to get the sound working through the headphonejack but not the internal speakers.   I tried both alsamixer, and pulseaudio cvolume control, but neither solved my problem .

Has anyone gotten it working?

---

### Post by linuxopjemac on 2010-11-09
You might want to try the following:
edit /etc/modprobe.d/alsa-base.conf
and make the line:
```
options snd-hda-intel power_save=10 power_save_controller=N
```
look like:
```
options snd-hda-intel power_save=10 power_save_controller=N model=imac27
```

instead of imac27 you could also try mbp55

---

### Post by c@ssie on 2010-11-09
> **linuxopjemac said:**
> You might want to try the following:
edit /etc/modprobe.d/alsa-base.conf
and make the line:
```
options snd-hda-intel power_save=10 power_save_controller=N
```
look like:
```
options snd-hda-intel power_save=10 power_save_controller=N model=imac27
```

instead of imac27 you could also try mbp55

There wasn't a line like it, so I added it at the bottom.  It didn't work with either imac27 or mbp55

---

### Post by theSuperman on 2010-11-10
After adding either the  imac27 or mbp55, did you restart and check alsamixer to make sure everything was unmuted? I had to mute and unmute a few times before it would work properly

---

### Post by c@ssie on 2010-11-14
> **theSuperman said:**
> After adding either the  imac27 or mbp55, did you restart and check alsamixer to make sure everything was unmuted? I had to mute and unmute a few times before it would work properly

Yes I did that, it still didn't work.
](*,)

---

### Post by Jboulden on 2011-02-21
I had the same issue with an iMac 20" 8,1 and found that this post solved the problem.
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

