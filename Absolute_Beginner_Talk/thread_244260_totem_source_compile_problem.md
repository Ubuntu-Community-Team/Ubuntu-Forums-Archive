---
title: "totem source compile problem"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by Kuraboy on 2006-08-26
Hi!

sorry if this is in the wrong place.

I was trying to compile totem from source because of that I wanted to have the same time skip for both left and right arrow.

okay, I downloaded 1.5.9 and typed ./configure

it wanted gcc, so I installed build-essential

then it wanted GStream dev package so I installed all the gstream dev packages I could find.

then I go this error:

```
checking for EXTRA_GNOME... configure: error: Package requirements (glib-2.0 >= 2.8.0 gtk+-2.0 >= 2.5.6 libgnomeui-2.0 >= 2.3.3 libglade-2.0 gnome-vfs-2.0 >= 2.8.2 gnome-vfs-module-2.0 >= 2.8.2 gnome-desktop-2.0 >= 2.1.5 gnome-icon-theme >= 2.9.3 gmodule-2.0 iso-codes gstreamer-0.10 >= 0.10.1 gstreamer-plugins-base-0.10 >= 0.10.7 gconf-2.0) were not met:

No package 'libgnomeui-2.0' found
No package 'libglade-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found
No package 'gnome-desktop-2.0' found
```

here was something weird. I checked these 5 not found packages but I found some on synaptic whith different names:

libgnomeui-2.0 on synaptic: libgnomeui-0
libglade-2.0 on synaptic: libglade2-0
gnome-vfs-2.0 on synaptic: libgnomevfs2-0
gnome-vfs-module-2.0 on synaptic: [couldn't find]
gnome-desktop-2.0 on synaptic: gnome-desktop-data

so what is wrong?! I have both universe/multiverse enable on synaptic. Am I doing someting wrong?

please any help is very appriciated, why havnt they made so that people can change properties of Totem player while runing it?

thnx in advance.

---

### Post by v1ct0r on 2006-08-26
Are you sure you installed all the required packages ?  That error is pretty self-explanatory. 

[http://www.gnome.org/projects/totem/](http://www.gnome.org/projects/totem/)

---

### Post by Kuraboy on 2006-08-26
the page says it needs Gnome 2.10, Gstream 0.10 and Gromit which I have all installed.

so I dont know why I get the error message. :(


beside, when the error says something like: glib-2.0 >= 2.8.0

dose it means I have to install glib-2.0? or that I have 2.0 but need 2.8.0? 

in synaptic I have libglib2.0-0 version 2.10.3-0ubuntu1

thnx

---

