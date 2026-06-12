---
title: "creating folder shortcuts"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by klep on 2007-02-08
Hello, 

this is a very simple question... how can i create a shortcut via the command line rather than the gui? and once it's created can i follow it in the commandline?


thanks

klep

---

### Post by steve.horsley on 2007-02-08
ln -s real-file-name link-name
e.g.
cd /usr/local/bin
ln -s /opt/ut2004/ut2004 ut2004

see man ln for details (that's a lower-case L, not a 1 or an I).

---

### Post by K.Mandla on 2007-02-08
Hi klep. I think this might work for you.

```
ln -s /path/to/destination /path/to/link
```
So for example, if you want a link from /home/kmandla/downloads to a folder called /home/kmandla/music and you want the link to be called "shortcut," it would be

```
 ln -s /home/kmandla/music /home/kmandla/downloads/shortcut
```
You follow it just by changing into the directory.

```
cd /home/kmandla/downloads/shortcut
```
That should take you to /home/kmandla/music.

---

### Post by klep on 2007-02-08
brilliant, thanks guys

---

