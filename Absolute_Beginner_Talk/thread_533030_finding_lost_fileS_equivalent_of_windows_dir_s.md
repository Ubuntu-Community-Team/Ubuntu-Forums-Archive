---
title: "finding lost fileS: equivalent of windows dir /s ?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-08-23
I've lost a file whose name I know - surely there's a command for searching systemwide to see where it was put by the install procedure? 

The file name is libmp3lame.so and yes, I had to install lame to get the mp3 exporting in audacity to work- but where did the lame install put the file I need, namely libmp3lame.so?

---

### Post by vambo on 2007-08-23
```
locate <file_name>
```

---

### Post by rexy on 2007-08-23
alternatively find -name <whaticantfind> works

---

### Post by ginestre on 2007-08-23
Thanks a million!

---

