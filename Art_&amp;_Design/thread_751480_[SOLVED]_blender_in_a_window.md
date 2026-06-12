---
title: "[SOLVED] blender in a window"
date: 2008-04-10
forum: Art &amp; Design
---

### Post by Tyke91 on 2008-04-10
can anybody help me with this? I'm trying my best to learn how to use blender, and I'm following a few online tutorials. the tutorials are GREAT, but I'd like to have them in the same view as blender. I have a fairly large monitor, and I was wondering how to get blender to go into a window so that I can view firefox and blender at the same time

---

### Post by Tyke91 on 2008-04-10
hmm... blender windowed mode works as long as I'm not using compiz-fusion... this may be a problem because I use AWN dock pretty intensively...

has anyone figured out how to run blender in a windowed mode with compiz-fusion?

---

### Post by Tyke91 on 2008-04-10
Not quite a permanent fix, but definitely a short term solution.

If you shut off compiz, awn will hide. Then you can start blender in a window. After blender is up, restart compiz. blender will stay in its windowed mode and awn will come back.

---

### Post by buried on 2008-04-11
Right then you fixed the problem your self :)

---

### Post by Tyke91 on 2008-04-11
yep, and there's a separate thread with a shell script that will do this. (I started it because I couldn't find any threads that had a solution)

[http://ubuntuforums.org/showthread.php?t=751600](http://ubuntuforums.org/showthread.php?t=751600)

---

### Post by ebharv on 2008-06-22
Or you can leave all your goodies running and follow one of these posts:
[http://ubuntuforums.org/showthread.php?p=5239564#post5239564]("http://ubuntuforums.org/showthread.php?p=5239564#post5239564")
[http://ubuntuforums.org/showthread.php?t=598971&highlight=blender+won%27t+run+window]("http://ubuntuforums.org/showthread.php?t=598971&highlight=blender+won%27t+run+window")

---

### Post by hessiess on 2008-06-22
run it using
```
blender -w
```
I haven't verified this, but it is lickly that running compiz will reduce Blenders view port performance. as compiz will be using some of your 3D cards cycles and ram that would have been used by blender.

---

