---
title: "[SOLVED] GStreamer/Totem DVD Problems"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Promaster91 on 2008-02-27
I am having trouble with totem dvd player, Ok, so I put my Simpson DVD in my computer and a message comes up saying I have to install the "ugly" plugin. So I do but when I try to play the DVD again is comes up with this error message...

"Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc. Please install the necessary plugins and restart Totem to be able to play this media"

I thought I just installed the plugin. Can anybody help me? Thanks.

---

### Post by jan quark on 2008-02-27
try this

```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

and open your dvd with gxine

---

### Post by Iehova on 2008-02-27
Totem gstreamer has issues with DVDs. I recommend going to synaptic and installing totem-xine, it'll want to remove totem-gstreamer. Totem xine actually handles DVDs properly.

EDIT: Beaten to it... ;)

---

### Post by Promaster91 on 2008-02-27
Ok, I am trying that now.

---

### Post by Promaster91 on 2008-02-27
Ok, It shows the FBI warning and the FOX thing. But when it goes to the menu, it shows an error message...

An error occurred
The audio device is busy. Is another application using it?

...What is going on?

---

### Post by Promaster91 on 2008-02-27
OK I fixed it by going to Edit>Pref>Audio and selecting 4 Channel. Thanks for everybody's help.:):):)

---

