---
title: "Removing files"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by niko7865 on 2007-03-27
I want to remove all files with the .jpg extension from a directory and all it's sub directories. Something like 'rm -r *.jpg' which of course wouldn't work. Any tips?

---

### Post by compmodder26 on 2007-03-27
Assuming you are in the correct directory that you want to start in.  That command would work fine if change the -r to -R so: "rm -R *.jpg"

---

### Post by Hossie on 2007-03-27
No, that wont work. The asterisk gets expanded by bash before it gets passed to rm. All jpeg in subdirectories won't get deleted.

You have to use something like (untested):

```
find . -iname "*.jpg" -exec rm {} \;
```

---

### Post by niko7865 on 2007-03-27
That worked great Hossie, thanks!

---

