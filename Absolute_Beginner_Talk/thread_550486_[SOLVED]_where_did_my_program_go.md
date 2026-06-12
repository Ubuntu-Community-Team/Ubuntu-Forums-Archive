---
title: "[SOLVED] where did my program go?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-09-13
I downloaded a .deb file from sourceforge, and it automaticly installed (at least it looked like it did). I cannot find any trace of the program in Applications. Where did it go??:(
Any help would be appreciated!!   Ubunu rocks:guitar:

---

### Post by ayenack on 2007-09-13
What was the program called? open a terminal and type the name of the program into it to see if it'll open.

---

### Post by nonewmsgs on 2007-09-13
if you selected open instad of save it would be in /tmp or /vars/tmp

---

### Post by steveneddy on 2007-09-13
In terminal

```
locate name_of_program
```

---

### Post by skyjacker on 2007-09-13
> **steveneddy said:**
> In terminal

```
locate name_of_program
```
Tried this and did not find any program by the name i downloaded. guess that means i really didnt install it huh?:confused:

---

### Post by sumguy231 on 2007-09-13
That could be because locate's database needs to be updated before you can search for something you just put on there (I believe the database is updated nightly, but it could be weekly or something) To force a database update:
```
sudo updatedb
```
This will take a while. When it's done, look again.

---

