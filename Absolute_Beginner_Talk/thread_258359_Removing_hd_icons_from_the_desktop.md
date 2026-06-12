---
title: "Removing hd* icons from the desktop"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by æþeling on 2006-09-15
Hi, I have two annoying icons on my desktop, named hda1 and hda2 (one on them is my windows partition, and the other one is a FAT32 partition I use to exchange files between Ubuntu and Windows.) Anyway, I'd like to remove them from the desktop, because they're blocking my beautiful background! So how could I do that?

---

### Post by Xappe on 2006-09-15
open gconf-editor:

alt+f2
type gconf-editor and click "Run"

go to:

apps --> nautilus --> desktop
and uncheck volumes_visible

that should do it.

---

### Post by æþeling on 2006-09-15
Thanks, that did it.

---

