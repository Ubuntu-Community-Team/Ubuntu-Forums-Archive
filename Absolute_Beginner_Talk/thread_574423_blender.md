---
title: "blender"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-12
hi,

i can't open my blender 2.43. I mean it's downloaded but if i double-click it it basically doesn't respond to it. So if double-click the icon and wait nothing happen. How can i resolve this problem??

thnx

---

### Post by bobplano on 2007-10-12
run 'blender' in the terminal (without the quotes) and post the output here

---

### Post by limac on 2007-10-12
hi,

ron@LIMAC:~$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.4.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: Unable to open Blender window
ron@LIMAC:~$ 

this was the output.

Thnx

---

### Post by bobplano on 2007-10-12
blender needs 3d acceleration for obvious reasons, and the drivers you are using don't support that. post your graphics card and current drivers

---

### Post by limac on 2007-10-12
hi,

I'm not sure about graphics card and drivers but in my opinion they aren't the cause since i did run blender on this computer under this ubuntu 7.04 before.

thnx

---

### Post by odd1here on 2008-02-28
having trouble with blender.
i ran it from terminal:
```

Compiled with Python version 2.5.1.
Checking for installed Python... got it!
Saved session recovery to /home/user/.blender/quit.blend

```

seems all go but, i get blank buttons, no characters and during mouse-over of interface 
it creates pixelized arrays of fragment artifacts.

would this have something to do with my version of python?
or possibly something related to python that i don't have?

i would really love to get this working correctly, i saw this being done about a year or so ago an fell in love:

[IMG]http://download.blender.org/demo/movies/arraydemo.jpg[/IMG]
[http://www.blendernation.com/2006/07/04/array-modifier-demo-video-and-blend/]("http://www.blendernation.com/2006/07/04/array-modifier-demo-video-and-blend/")
[http://www.geneome.net/blender/videotutorials/ArrayDemoExplained-XviD.avi]("http://www.geneome.net/blender/videotutorials/ArrayDemoExplained-XviD.avi")
(10.7 MB Xvid - remember to right click and Save As).

[http://www.youtube.com/watch?v=Ymfn3fc8LGw&feature=related]("http://www.youtube.com/watch?v=Ymfn3fc8LGw&feature=related")

---

