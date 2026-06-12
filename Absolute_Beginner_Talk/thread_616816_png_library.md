---
title: "png library"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by edwin_cheung88 on 2007-11-18
I'm getting an error on my png library

configure: error: You must have the png library installed to compile the client

sudo apt-get install libpng gets me nothing, so I'm just asking on what the png library is called

---

### Post by Arthur Archnix on 2007-11-18
One way is to search using "apt-cache search", e.g.,
```
sudo apt-cache search png
```

---

### Post by edwin_cheung88 on 2007-11-18
configure: error: You must have the png library installed to compile the client

I have done sudo apt-get install libpng12-0 and it's still giving me this error

---

### Post by Arthur Archnix on 2007-11-18
Perhaps you could post a link to the instructions you're following and what you're trying to achieve. It looks like you're trying to compile something, and in that case it could be something as simple as creating a symlink to an already existing png library on your computer.

---

### Post by Paul820 on 2007-11-18
To compile something and you get errors, when it says it can't find the files it means the development files, so you have to install
> sudo aptitude install libpng12-dev

---

