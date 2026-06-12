---
title: "No Sound For MacPro4,1 running Ubuntu 10.04 LTS"
date: 2010-11-01
forum: Apple Hardware Users
---

### Post by jsmidt on 2010-11-01
I am running Ubuntu 10.04 on a MacPro4,1.  I don't get any sound.  Anybody have any ideas or things I can test?  Thanks.

---

### Post by linuxopjemac on 2010-11-02
did you try to unmute the channels with
```
alsamixer
```
(unmute with the m key)

---

### Post by jsmidt on 2010-11-02
linuxopjemac,

Yes, I unmuted everything with alsamixer and turned the volume as high as possible and I get nothing.

---

### Post by linuxopjemac on 2010-11-03
then there is a problem. I would Google and file a bug report against Alsa.

---

### Post by kernel_script on 2010-11-03
[From the wiki]("https://help.ubuntu.com/community/MacPro"):

> "For the HDA Realtek ALC885/intel sound, the default installation does not enable sound output. An easy solution is to edit:

sudo gedit /etc/modprobe.d/alsa-base.conf

and add at the end:

options snd-hda-intel model=imac24

This is the only option that works. Other model=macpro is not effective. Currently Only the back sound output port is working properly. The front audio port does not output at full volume. Better than nothing :-)) ."

For me (Macmini4,1), what worked was =mbp55

You can try these and see if it works. If it doesn't, you can just remove the lines.

---

