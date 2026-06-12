---
title: "help with Jdk"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by tin2 on 2006-12-25
I have installed jdk using automatix.
One program i need to install needs to know in which folder jdk is installed...but i cant figure it out.Where can it be?

---

### Post by DaveBorealis on 2006-12-25
> **tin2 said:**
> i need to install needs to know in which folder jdk is installed

Hello,

Open a terminal and type:
```
 sudo /usr/bin/updatedb
```
This will update the 'locate' database.

Then in the terminal type:
```
locate java | less
```
And  the space bar will page you  through the location of various java files and folders/directories.  (The 'b' key will move you back a page.)

HTH,
Dave

---

