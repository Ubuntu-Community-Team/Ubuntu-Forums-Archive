---
title: "getlibs for other file types?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Luksion Knight on 2007-08-30
i know getlibs command solves dependency problems with binary files, but is there a similar command that solves dependency problems with other file types like shell scripts or make files?

---

### Post by Cappy on 2007-09-26
Hey, I would have gotten to this a lot faster if you had asked in the getlibs thread.

with getlibs you can do ```
sudo getlibs -32 libraryname.so.0
``` for instance to download a missing 32-bit library on a 64-bit system.

Now if you want a program that solves dependencies automatically for shell scripts you need auto-apt
```

sudo apt-get install auto-apt

```
Auto-apt can find what libraries are missing in shell scripts but it can only download NATIVE libraries (through apt-get). So if you need a 32-bit library and you are running 32-bit ubuntu it will work perfectly.

You may want to look into apt-file for make files. I often 
```

apt-file search missingfileheaderwhilecompiling
```
to identify the packages I am missing. There might be another way - I don't need to compile often.

---

