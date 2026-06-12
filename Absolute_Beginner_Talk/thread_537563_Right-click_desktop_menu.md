---
title: "Right-click desktop menu"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by xtapolapaktl on 2007-08-29
I've run into a tiny problem that I have a hard time finding a solution to.

Some time ago, back when I had the Edgy installation of Ubuntu, I managed to get a new entry to the right click desktop menu, which would open a new terminal. Since then, I've upgraded to Feisty and the link causes my computer to hang.
So the thing is, I've forgot how I got the entry there in the first place, and can't seem to find any guides except the ones concerning the nautilus-open-terminal package, which I don't use anyway.
The question is, what/where do I edit to remove this entry ?

The menu looks like this:
Create Folder
Create Launcher...
Create Document ->
---------------------
Open Terminal                (this is what I want removed)
---------------------
...


thanks in advance.

---

### Post by Xyhthyx on 2007-08-29
```

sudo apt-get remove --purge nautilus-open-terminal

```

---

### Post by Zalbor on 2007-08-29
EDITED OUT: Damn, ignore me. What's wrong with me today?

---

