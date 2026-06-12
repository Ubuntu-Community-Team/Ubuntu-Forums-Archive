---
title: "control volume at command line"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by vertex78 on 2007-10-30
Is there a way that I can turn the volume up or down on my laptop from the command line?  I am running ubuntu 7.10

---

### Post by kaptengu on 2007-10-30
Try alsamixer.

---

### Post by ddrichardson on 2007-10-30
amixer.```
amixer -c 0 sset PCM,0 80%

```
do a man amixer for more examples.

---

### Post by Seisen on 2007-10-30
Just type alsamixer in the terminal.

---

### Post by vertex78 on 2007-10-30
ok, I did a man search on it read up on it.  Is there anyway to make it so the volume control  setting also gets changed? For instance I can set my volume to 10% but the volume control in the taksbar will still show it at 100%

---

### Post by wickedlester on 2007-10-30
try using "Master" instead of "PCM"

amixer -c 0 sset Master,0 80%

---

