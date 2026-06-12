---
title: "Totem problems (weird window behavior)"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Nergar on 2007-10-22
Weird thing is happening to me when i open totem, I cant resize, move or minimize the window.
It looks like it is in fullscreen mode AND maximized without window borders AT the same time. Videos Play normally though.

heres the shell output :

```
nergar@nergar-lap:~$ totem
      
** (totem:5877): CRITICAL **: bacon_video_widget_set_fullscreen: assertion `bvw != NULL' failed

** (totem:5877): CRITICAL **: bacon_video_widget_set_show_cursor: assertion `bvw != NULL' failed
JACK tmpdir identified as [/dev/shm]

```

Hope you can help me Thanks!

---

### Post by cfaulkner on 2007-10-22
can you click the Close Fullscreen button? top right?\

---

### Post by Tatty on 2007-10-25
im having exactly the same problem :(  its just started happening today when my gf was playing some videos... 

Cllicking on leave fullscreen has no effect. :confused:

---

### Post by jf1991999 on 2007-10-25
I am also having exactly the same problem.  There isn't any way to resize the window.  I tried closing and reopening but it just comes back to full screen mode.  It overlaps both the top and bottom panels.

---

### Post by Tatty on 2007-10-30
Hurrah! I managed to fix this problem by turning compiz off then on again via System->Preferences->Appearance->Visual Effects

:popcorn:

---

### Post by BootROM on 2007-11-03
Thanks Tatty, I had this exact same problem and that fixed it. Cheers :)

---

### Post by aeg1s on 2007-11-04
I have the same problem PLUS sometimes when I go to fullscreen totem just closes/disappears...  Very odd...

---

### Post by Nergar on 2007-11-07
bump!

The fix described above doesnt work for me :(

Clicking on the fullscreen button doesnt work

---

### Post by Nergar on 2008-04-30
bump! :P
new, fresh installation of hardy and after watching some videos im having this prolem again.

---

### Post by r0nin on 2008-06-03
If you switch the sidebar off you can resize the window again. Annoying, but that works :(

---

