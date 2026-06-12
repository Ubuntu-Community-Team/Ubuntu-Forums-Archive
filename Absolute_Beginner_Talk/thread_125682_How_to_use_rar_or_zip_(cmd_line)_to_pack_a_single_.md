---
title: "How to use rar or zip (cmd line) to pack a single cd-ISO file to 50MB files ?"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-02-04
Nota: (without using split )

Thank  you !!

Greetings from Belgium , 

Patrick

---

### Post by joselin on 2006-02-04
Try this:

> man rar

or this:

> man zip

---

### Post by patrick295767 on 2006-02-05
Thx, 

I did already but didnt manage with ```
rar a -v 2000B archive.rar  file_big_one_topack.img
```

 where is it wrong somewhere ?

---

### Post by damian.rohraff on 2008-04-06
Kind of late, but maybe will help :)
```
rar a -v51200k -m0 -md4096 -rr -t /home/user/folder/file.rar /home/user/folder/file.iso

```

---

