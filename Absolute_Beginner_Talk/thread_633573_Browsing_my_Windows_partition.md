---
title: "Browsing my Windows partition"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by ChunkOFunk on 2007-12-06
So, I'm running Gutsy and I love it, everythings pretty, everything works. Wonderful. But, the issue that I run into, is that I can't seem to browse my windows partition fully. I can kinda get there, but I can't get into things like my program files, which is what I really want to do so that I can run my games and such with Wine. Anybody have any ideas why this is not letting me into my program files? Or, best case scenario is that someone can post a file path to that location. Thanks

---

### Post by PeterJS on 2007-12-06
What do you mean not browseable? Is this from the command line or a graphical file browser? If it's from the command line it's probably the space in "Program Files" that's causing the problem. To get in to program files you need to some how tell the terminal that the space is part of the directory name, and not a separator between directory names. You could try:
```

cd "Program Files"

```or
```

cd Program\ Files

```Also tab completion works really well here, it will properly escape the space for you. This really needs to go some where in bold letters some where hard to miss: **When using the terminal use tab completion, it will save you keystrokes and fill in things when you don't know the exact name of what you're looking for.**

---

