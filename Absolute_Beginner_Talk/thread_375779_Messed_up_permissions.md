---
title: "Messed up permissions"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by steel_lady on 2007-03-04
I accidentally did chmod 777 on my home. Later I did 755. And now I can not lounch some programs like Amule. How can I mend it and not to consider permissions file by file? I am an absolute beginner

---

### Post by laidback on 2007-03-04
There is a recursive switch on chmod,  -R. Type chmod --help in a terminal for more help.
So if you want to change an entire directory and all files within it including subdirectories it appears to be possible.

---

### Post by steel_lady on 2007-03-04
Yes I did it recursively. That's why programs are not working now!

---

### Post by laidback on 2007-03-04
Deleted

---

