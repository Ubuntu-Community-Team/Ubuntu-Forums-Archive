---
title: "wmv codec??"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by MSlaveubu on 2007-02-02
I have tired the:

```
sudo aptitude install gstreamer0.10-pitfdll && rm -r ~/.gstreamer-0.10/
```

but it still doesnt work?

can anyone shed some light?

---

### Post by the_darkside_986 on 2007-02-02
I don't how much I can help with gstreamer but for all other movie players, I downloaded the dlls from mplayer headquarters and put them in /usr/lib/win32

MPlayer and xine all worked after that but I don't know if that is gstreamers problem. You could try to put the mplayer dlls wherever gstreamer looks for codecs. I don't know if that will work or not for gstreamer.

---

### Post by OldTimeTech on 2007-02-02
if you use synaptic, search for gstreamer, you can load it from there.

if you need other files with gstreamer, synaptic will show them.

If you need codecs and such, maybe you need to use automatix2.

---

### Post by Bigadada_saba on 2007-02-02
if you isnstal automatix and then from automatix instal audio and video codecs every thin should ru fine
 i you stil have aproblem install vlc mediaplayer

for automatrix instalation check this link out
[http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38]("http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38")

---

