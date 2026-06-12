---
title: "youtube working with cvs gnash"
date: 2007-05-31
forum: Apple PPC Users
---

### Post by stmiller on 2007-05-31
Okay I built gnash from CVS 5.30.07 and youtube video plays back in PPC Linux in Firefox. I configured it like this:

```
./configure --enable-renderer=Agg --enable-media=GST

```

which required compiling agg 2.5 from source since ubuntu doesn't have that version.

[http://www.antigrain.com/download/index.html](http://www.antigrain.com/download/index.html)

Other configuration options (opengl, ffmpeg, mad, etc.) did not work for me for the plugin.

Also, when playing back youtube, the cpu is at 100%. But video playback and audio is good.

Anyways, those are some comments! I think the next gnash release is coming as soon as youtube is stable.

---

### Post by eugoss on 2007-05-31
Thank you! That's a good news! They are definitely improving it :)

---

### Post by ubuntubrian on 2007-06-09
good news!
I ran make in the agg directory but "make install" returns "nothing to be done for install".
Is that it?
Just want to start out right!
:)

---

### Post by ubuntubrian on 2007-06-09
We'll see if I did this correctly. I ran:
./autogen.sh
automake
makeinstall 

and something seems to be working.

---

### Post by ubuntubrian on 2007-06-09
And gnash works!!
thanks for the info:p

---

