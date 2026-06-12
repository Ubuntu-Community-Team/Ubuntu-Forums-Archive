---
title: "Allowing Ubuntu to write on Mac Partitions"
date: 2009-07-31
forum: Apple Hardware Users
---

### Post by Whamola on 2009-07-31
Hey everyone, I assume this question has been answered, so I'll get right to it.

In 8.04 (or 9.04 if that's easier), how can get both a mac drive (10.5.7) and a mac formatted external hard drive (used as time machine)?  I am trying to get the files off the external on to the internal, then reformat the external, all in ubuntu.

---

### Post by Whamola on 2009-07-31
Hate to do this, but bump.

---

### Post by WillJeffery on 2009-08-01
Bump. I would also like to know the answer to this.

---

### Post by edmondt on 2009-08-02
I could be wrong, but I think it is something to do with getting the same uid on osx and ubuntu, check the stickies on how to install ubuntu on macbook

---

### Post by wayne_cat on 2009-08-02
You can only write on Mac partitions if their journaling is disabled. HFS+ partions
with journaling can only be mounted read_only.

---

### Post by schauerlich on 2009-08-03
Install hfsprogs, and disable journaling on the HFS+ drive.

---

