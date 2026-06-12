---
title: "Sound sometimes works"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by tjd_maximum on 2008-04-09
Hello,
I'm having trouble with my sound. Sometimes when I boot it up I get sound, but the majority of the time I do not. Right now I do not have sound but it seems like Ubuntu is still recognizing my audio card (it is showing up in the device manager). The card is "MCP51 High Definition Audio" and the vendor is nVidia. Does anyone know anything about this? Is there a way I can find out what is going on differently when I do have sound so I can find out what is going wrong the rest of the time?

EDIT: Sorry, I'm using Ubuntu 7.10

Thanks.

---

### Post by TheLions on 2008-04-09
the most probably cause is that you have muted some sound chanells, open terminal and install sound manager:
```
apt-get install alsamixer
```

then unmute all channels and increase volume to max

or

you have 2+ installed soundcards...

---

