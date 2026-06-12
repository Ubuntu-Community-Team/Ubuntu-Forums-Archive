---
title: "Sun Java and updates problem"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by novice1969 on 2008-03-04
I wanted to play most common multimedia formats, including MP3, DVD, Flash, Quicktime, WMA and WMA.  I went to the official Ubuntu Documentation website and it said to use this command in terminal.

sudo apt-get install ubuntu-restricted-extras

Everything looked like it was going smoothly until I got the following:


It just kind of hung up there in terminal and then updates wouldn't work after that.  How do I fix this problem?

---

### Post by kellemes on 2008-03-04
Open a terminal and type..
```

sudo dpkg --configure -a

```

---

