---
title: "How Do I Add an Icon?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by wmichaelb on 2007-05-01
Hi, I've searched through the posts but been unable to find an answer to this question. I installed Xarclock, but keep getting this error message because there is no icon for it. How do I add an icon to usr/share/pixmaps? The system won't let me simply copy an icon to this folder.  Is there a "copy"-like command in Ubuntu that can be accessed from Terminal?

Thanks!

---

### Post by lamalex on 2007-05-01
```
 sudo cp /source/file /usr/share/pixmaps/file
``` is copy in terminal into the pixmaps

---

### Post by stump138 on 2007-05-01
you can try

```
sudo cp /path/to/bitmap /path/to/where/you want/it
``` :)

---

### Post by stump138 on 2007-05-01
lol Iamalex beat me to it :)

---

### Post by wmichaelb on 2007-05-03
Lamalex: When I try this with "/home/mike/pix/gnome-xarclock.png", I get an error message that says "no such file or directory". Is there something else I'm missing in the file address? 

Thanks again.  I have a very little exposure to Unix; but there are some really basic things in Linux that I just don't get yet.

---

### Post by wmichaelb on 2007-05-06
When I copy the correct spelling of the various file names, it works! Thanks to all.

---

