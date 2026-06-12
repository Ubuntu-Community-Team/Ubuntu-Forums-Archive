---
title: "Problem playing video files"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by umesh on 2007-05-27
I used VLC for playing avi and wmv format and other different types of divx files but I see no visual, hear only sound. Is anything missing or do I need to install some more codec or what? appreciate your help in this regard.

Umesh

---

### Post by seshomaru samma on 2007-05-27
which codecs did you install?
try this:
```
sudo aptitude install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good \
gstreamer0.10-plugins-bad gstreamer0.10-pitfdll w32codecs

```

---

### Post by Nordoelum on 2007-06-08
This won't work for me. Can't play .wmv files. Totem only closes after getting in fullscreen.

---

