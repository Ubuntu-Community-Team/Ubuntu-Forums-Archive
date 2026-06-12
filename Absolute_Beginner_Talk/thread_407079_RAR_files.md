---
title: "RAR files"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2007-04-11
I'm just wondering what everyone uses for extracting RAR files, specifically chunked rar files. I've tried Archive manager and Ark, both of which seem unable to unzip the files, could somone give me advice one a program that does do these well or a way to make these programs extract chunked rars well. Thanks

---

### Post by taurus on 2007-04-11
You just have to unpack the first one from a terminal and it knows how to handle the rest.

```
unrar x first_file.rar
```

---

### Post by devnulljp on 2007-04-11
on the command line:

unrar e filename.rar will extract to current directory
unrar x filename.rar will extract wit full path
unrar l will list files

Try man unrar

---

