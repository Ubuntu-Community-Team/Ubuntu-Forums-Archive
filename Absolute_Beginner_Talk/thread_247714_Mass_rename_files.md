---
title: "Mass rename files"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by jessexoc on 2006-08-31
How do you mass rename files from the command line? I have a bunch of mp3's with filenames like:
**Artist_-_Album_-_TrackNumber_-_Track_name.mp3**

I want to convert all the "_"(underscore) to " "(space). I tried:
**$ for i in *; do mv "$i" `echo $i | tr '_' ' '`; done**

but it complains that:
**mv: target `name.mp3' is not a directory.**

What am i doing wrong?

---

### Post by Jussi Kukkonen on 2006-08-31
The problem is the whitespace -- when filenames with spaces are given to commands, all instances of space should be escaped, as in:
```
ls Artist\ -\ Album\ -\ TrackNumber\ -\ Track\ name.mp3
```
Your mv command doesn't have those.

Sometimes quotes work too:
```
for i in *; do mv "$i" "`echo $i | tr '_' ' '`"; done
```
Should do it.

---

