---
title: "I cannot extract an RAR archive"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by Ob1 on 2006-03-24
I get this error message

> Could not open "1001.dsr-loki.r00"

Archive type not supported.

And these are 10 RAR files all contain a avi files who are realted to each other, i think it's called a chain files, please help.

---

### Post by trent dillman on 2006-03-24
is there a *.rar file? and is there a password?

---

### Post by Jucato on 2006-03-24
Among those 10 rar files, one of them will have the .rar extension. You're supposed to extract that one, not the ones ending in .r00 or something. Extracting the .rar file will automatically extract and join together all the rest.

That is, presuming you have been able to extract .rar file before.

---

### Post by Ob1 on 2006-03-24
[QUOTE=Fenyx]Among those 10 rar files, one of them will have the .rar extension. You're supposed to extract that one, not the ones ending in .r00 or something. Extracting the .rar file will automatically extract and join together all the rest.

That is, presuming you have been able to extract .rar file before.[/QUOTE]

i have tried them all, my system probably can't extract .rar file.

---

### Post by arnieboy on 2006-03-24
try the following from terminal:
```
sudo apt-get install rar unace unrar-nonfree
```
and try unpacking the archive again

---

### Post by Ob1 on 2006-03-24
It works now, thanks.

---

