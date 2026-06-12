---
title: "totem movie player - strange colors"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by hlekat on 2008-02-07
i have installed :
libtotem-plparser7
totem
totem-gstreamer
totem-mozilla

the colors are false especially the blue.
with vlc player everything is fine but i cannot play subtitles.

with my previous installation i had the some problem in the beginning but i don't remember how i solved it.
is there anything i have to install ?

---

### Post by hlekat on 2008-02-07
no one?

---

### Post by hlekat on 2008-02-08
is there any codec i have to install except the one that ubuntu automatically asks to install? 

do i have to uninstall this one and install something else ?

---

### Post by seventhc on 2008-02-08
Not sure about the strange colors, but here is a link about using subtitles in VLC.
[http://www.videolan.org/doc/play-howto/en/ch03.html#id290015](http://www.videolan.org/doc/play-howto/en/ch03.html#id290015)
maybe that will help. :)

---

### Post by hapveg on 2008-02-15
Read somewhere there is a bug in the ATI drivers which swaps red and blue, can't find where I read it though.

Fix is below:

launch gstreamer-properties from terminal
change the video output plugin to custom
change the video output pipeline to:

ffmpegcolorspace ! video/x-raw-yuv,format=(fourcc)YV12 ! xvimagesink

from: [https://answers.launchpad.net/ubuntu/+source/totem/+question/7373](https://answers.launchpad.net/ubuntu/+source/totem/+question/7373)

---

### Post by oedha on 2008-02-15
have you setup the video preferences on totem.....because when i installed compiz, it was changed all to the left side....and the color just back and white....
second...it could be the effect of compiz....do you use compiz ?

---

### Post by hlekat on 2008-02-17
This was the problem. I try to fix it by removing programs and drivers, but nothing happen.
I changed the gstreamer properties and that fixed the problem.

I wonder why the problem was only with totem player .

---

