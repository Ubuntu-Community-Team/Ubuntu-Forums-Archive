---
title: "how to relocate swap to ram?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by cseljatib on 2007-11-20
I have not idea how, but i do have more swap memory than ram (As you can see in the picture). 
I would rather prefer to have more RAM than swap memory, but i do not know how to do it, Is it possible?, how?

please help me!!

thanks

---

### Post by jfinkels on 2007-11-20
Your "swap memory" is the size of the swap partition on your hard disk. Your operating system writes to the swap partition instead of to RAM only when it runs out of room in your RAM. (The idea is that writing to RAM is faster than writing to a hard disk).

You can resize your swap partition using a tool like gparted. To install gparted, type the following in the terminal:```
sudo aptitude install gparted
```

---

