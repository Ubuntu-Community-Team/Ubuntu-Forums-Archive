---
title: "How to delete links?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by japc126 on 2008-02-29
I created a link to starcraft.exe which was in my windows partition, and placed it in the desktop... but now I don't want it there, and it wont let me delete it!! What do I do?

---

### Post by taurus on 2008-02-29
What happens if you try to delete it from a terminal?

```
cd ~/Desktop
rm *name_of_the_link*
```

---

### Post by fs3rp4 on 2008-02-29
> **japc126 said:**
> I created a link to starcraft.exe which was in my windows partition, and placed it in the desktop... but now I don't want it there, and it wont let me delete it!! What do I do?

Open terminal

sudo rm ~/Desktop/LINK_NAME

---

### Post by japc126 on 2008-02-29
thanks, that took care of it

---

