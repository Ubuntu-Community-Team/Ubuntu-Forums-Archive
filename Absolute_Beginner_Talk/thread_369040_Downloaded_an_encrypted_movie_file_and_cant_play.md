---
title: "Downloaded an encrypted movie file and cant play"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2007-02-24
I looked at other posts, but they were mainly all about DVD encryption, this movie file is a wmv file and when I open it I get an error stating 'This file is encrypted and cannot be played"

I know that this file might require a password to view (for my online college classes), is there a way to get something to pop up so I can put the password in? Or maybe a player that works well with this?

---

### Post by Spr0k3t on 2007-02-24
You will need to do this if you haven't already:

```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
sudo aptitude install gstreamer0.10-pitfdll && rm -r ~/.gstreamer-0.10/
```

This information can be found here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

I know you are using Xubuntu, but I wonder if the same information applies.

---

### Post by Dirty Ole on 2007-02-24
Yes it applies to all Ubuntu variations. Xubuntu has XFCE as Window manager but the working is same as Ubuntu(Gnome).

---

