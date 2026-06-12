---
title: "about .run files"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-06-17
sone .run files installing the packages correctly but some are displaying this massage :
"gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

I've tryied to change the coding but it still showed the same problem
what do I do ?
it is a very important package.

---

### Post by x64Jimbo on 2006-06-17
Wait, you're trying to edit these run files with gedit?

---

### Post by MaximB on 2006-06-17
it just open them with gedit - no questions ask...
what I suppose to do ?

---

### Post by atomicSpatule on 2006-06-17
[QUOTE=MAXDDARK]it just open them with gedit - no questions ask...
what I suppose to do ?[/QUOTE]

You have to open a console, browse to the directory where the *.run file is then  write :
```

$ chmod +x [file].run
$ ./[file].run

```
You have to replace [file] by the name of the file

---

