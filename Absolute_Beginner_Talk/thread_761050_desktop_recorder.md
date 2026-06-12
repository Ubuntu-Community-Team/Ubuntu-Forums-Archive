---
title: "desktop recorder"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-04-20
i need one that can download just a window.
are there any for linux that do anything besides .ogg file type
because i can't figure out how to convert it to a like .mpg or something
that can be posted onto youtube...

---

### Post by Ryutatsu on 2008-04-20
I use gtk-recordMyDesktop and then transcode using mencoder. The command for that is:

mencoder <input filename>.ogg -o <output filename>.avi -oac mp3lame -ovc lavc

---

