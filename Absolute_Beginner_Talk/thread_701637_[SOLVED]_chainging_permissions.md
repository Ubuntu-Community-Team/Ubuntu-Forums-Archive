---
title: "[SOLVED] chainging permissions"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Tek-Noir on 2008-02-19
Id like to change the permisions of this folder so anyone can access and read and write to it. Could some one tell me what the command would be? 

/usr/local/games/quake3

---

### Post by justleen on 2008-02-19
in a terminal:
```
 sudo chmod a+rw /usr/local/games/quake3 -R
```

 a=all  rw=read/write

-R is recursive in this case (meaning it wil go into sub folders)

---

### Post by Tek-Noir on 2008-02-19
Brilliant, thanks. Been trying to find the answer to that for ages now lol

---

### Post by Tek-Noir on 2008-02-19
Just so i know for in future, how would you do the opposite?

---

