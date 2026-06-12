---
title: "msttcorefonts?!"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Znupi on 2007-04-21
Well I've read in the docs that to get M$'s fonts (Arial etc) you need to install the msttcorefonts package... This is what I get:
```

$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

```
I'm using Ubuntu 6.06 - Dapper Drake and yes, I have the multiverse repository activated.

---

### Post by steve.horsley on 2007-04-21
I'm on Feisty at the moment so I can't be sure about Dapper, but I Feisty, msttcorefonts is in Multiverseand I doubt it has moved, so it looks like you're doing the right things. I know I used msttcorefonts in Dapper without problems.

All I can suggest is that you try **sudo apt-get update** to re-read the repository indexes.

---

### Post by heimo on 2007-04-21
It seems to be in multiverse. 
[http://packages.ubuntulinux.org/feisty/x11/msttcorefonts](http://packages.ubuntulinux.org/feisty/x11/msttcorefonts)

Add multiverse using these instructions:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Znupi on 2007-04-23
> **heimo said:**
> It seems to be in multiverse. 
[http://packages.ubuntulinux.org/feisty/x11/msttcorefonts](http://packages.ubuntulinux.org/feisty/x11/msttcorefonts)

Add multiverse using these instructions:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Thanks heimo, that did it. Although, the fonts are a bit small, and they look 'squeezed'. Is that normal? Is there any way to fix it?...

---

