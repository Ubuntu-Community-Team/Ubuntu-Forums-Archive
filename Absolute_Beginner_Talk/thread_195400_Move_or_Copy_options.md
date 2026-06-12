---
title: "Move or Copy options?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by renis on 2006-06-12
How do I tell ubuntu to copy a file to a folder or move it.

---

### Post by taurus on 2006-06-12
```

mv <filename> /to_where_you_want_to
cp <filename> /to_where_you_want_to
-or-
man mv
man cp

```

---

### Post by renis on 2006-06-12
is there any easier way?
thanks

---

### Post by taurus on 2006-06-12
What do you mean an easier way?  You can always use nautilus and do your drap 'n drop if typing from a terminal is a little too hard to do!

---

### Post by renis on 2006-06-12
lol taurus

its just that i have a LOT of fille organizing to do and that would way to much typing

---

### Post by taurus on 2006-06-12
if you want to move all the files in one directory to another, use the * sign.  And if you want to move only a handful of files but they happen to have the same extension, then do something like
```

mv * ~/new_place
-or-
mv *.txt ~/new_place

```
If you can tell me a little more about those files, names, I can tell you an easy way to move them around...  Once you know the basic structure, terminal is quite fun to use.  I do all my work from terminal.  :)

---

### Post by renis on 2006-06-12
Thanks
I am moving mp3's mostly
Some pictures, .JPG

---

### Post by taurus on 2006-06-12
Do you want to move all of them or only a certain pictures or songs?  If you want to move all of them, then one command will do...
```

mv * ~/new_place

```

---

### Post by renis on 2006-06-12
each color is a different kind of file
before/after
[IMG]http://img98.imageshack.us/img98/3552/folders1ul.jpg[/IMG]

---

### Post by taurus on 2006-06-12
Hey, thanks for the drawings.  :) 

I suppose you want to move all the pictures, .jpg, to a same directory so you can use the *.jpg (or *.JPG) in place of the names.  On the other hand, I assume you want to move certain songs to one directory while some others to another directory.  I guess you just have to use nautilus or some other file managers to drag 'n drop then.

---

