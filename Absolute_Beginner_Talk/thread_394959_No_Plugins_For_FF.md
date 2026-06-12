---
title: "No Plugins For FF"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by dothedorky on 2007-03-27
Hello all.

After a hard drive failure, i transferred data from the old HD to a new barracuda HD which left me with more room to work with. 

I finally deleted my windows paritition entirely (never really used it anyways) and set up a clean, bareboned edition of 6.06 LTS.

One problem, my about:plugins query, when entered in the search bar, tells me there are NO plugins installed whatsoever. I've tried the walkthrough on psychocats, and was unsuccessful in making flash (or any other plugin) to function correctly. 

Is there any quick, and fool proof ways to get all the plugins i need installed on FF (mainly flash)?

Any help would be greatly appreciated

---

### Post by Bachstelze on 2007-03-27
```
sudo apt-get install flashplugin-nonfree
```

should install Flash in your Firefox, at least it did for me, with no additional configuration needed.

---

### Post by aysiu on 2007-03-27
> **HymnToLife said:**
> ```
sudo apt-get install flashplugin-nonfree
```

should install Flash in your Firefox, at least it did for me, without no additionnal configuration needed.
That will work if you [have the Multiverse repositories enabled.](http://www.psychocats.net/ubuntu/sources)

Otherwise, [this quick tutorial](http://www.psychocats.net/ubuntu/flash) will work.

---

