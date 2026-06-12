---
title: "[SOLVED] Scripting Question, I've Tried Everything!!!"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by MrFSL on 2007-04-29
I am working on a project where a person would doubleclick on a scipt and it would open a terminal, display some information, and leave the terminal open so a person could keep using it. Similar to "cmd /k" in windows. The problem is that I can't keep the terminal open. I can pause it with "read" or "sleep" but thats not what I am trying to do. I just want it to open a terminal... print a message in the terminal... and leave the terminal open for additional input. Any clue?

I have read the man pages and info pages for xterm, aterm, gnome-terminal, xfce4-terminal, etc... I have searched google and this forum.

Someone give me a hand?

This can be a perl script, or a bash script... i dont care which.

Thank In Advance.

MrFSL

---

### Post by [S|G] on 2007-04-29
```

#!/bin/bash
bash

```
:)

---

### Post by MrFSL on 2007-04-29
Thank You for your quick reply but I don't think I understand. This opens a terminal and leaves it open but how do I display text in that open terminal? you need what I mean?

Thanks.
MrFSL

---

### Post by MrFSL on 2007-04-29
Ah I figured it out.

#!/bin/bash
echo Hello World
bash


Thanks

MrFSL

---

