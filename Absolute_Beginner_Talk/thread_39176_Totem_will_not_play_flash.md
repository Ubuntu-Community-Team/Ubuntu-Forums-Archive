---
title: "Totem will not play flash"
date: 2005-06-03
forum: Absolute Beginner Talk
---

### Post by kozmo on 2005-06-03
When I try to play a flash video in Totem I get an error:

[B]Totem could not play the file: python_01.swf

There were no decoders found to handle the stream in file "file:///home/jimmy/python_01.swf", you might need to install the corresponding plugins.[/B]

However, the same flash video plays just fine in FireFox.

---

### Post by vega44 on 2005-06-03
you don't have the plugins needed to play swf files.i dunno where to find the plugins...

try google

---

### Post by poofyhairguy on 2005-06-03
[QUOTE=kozmo]When I try to play a flash video in Totem I get an error:

[B]Totem could not play the file: python_01.swf

There were no decoders found to handle the stream in file "file:///home/jimmy/python_01.swf", you might need to install the corresponding plugins.[/B]

However, the same flash video plays just fine in FireFox.[/QUOTE]

Well. First I think you need the free flash pluggins for that to work:

sudo apt-get install swf-player gstreamer0.8-swfdec

Note that it might not work as well as in Firefox because the non OSS flash pluggin is very closed so the OSS flash pluggin suffers because of that.

---

