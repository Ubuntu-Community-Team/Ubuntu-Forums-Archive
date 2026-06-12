---
title: "spaces in folder names"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by gorlop on 2007-03-23
In Terminal, how do I refer to a folder with a space in its name. For example, I can't  access the folder "My Stuff" by typing the following:

cd My Stuff

I changed the name of the folder to "mystuff" and typed:

cd mystuff

...and this works fine, but I don't want to have to do this with every folder.

---

### Post by compmodder26 on 2007-03-23
either put the folder name in quotes or put a \ in front of each space in the folder name

---

### Post by kpkeerthi on 2007-03-23
Type 'cd My' and press [TAB]

---

### Post by AndrewBarber on 2007-03-23
```
cd ./My\ Stuff/
```

Or you could use tab complete as specified.

---

### Post by gorlop on 2007-03-23
Thanks.  The Tab option is especially useful.

---

