---
title: "Lexmark X1180 not working!!"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by miggols99 on 2007-03-31
I tried using [this page]("http://www.ubuntuforums.org/showthread.php?t=49714&highlight=X1150.") to install my Lexmark printer, but it didn't work. The Z600 driver came up when I was trying to set up the printer, but the printer did nothing. Does anyone know how to fix this?

Output of ./z600

```
./z600: error while loading shared libraries: liblexprinter.so.0: cannot open shared object file: No such file or directory

```

Don't worry. I fixed it :)

---

### Post by chili555 on 2007-03-31
I wonder if it should actually be: *sudo ./z600*?

---

### Post by Realsoz on 2008-06-01
> **miggols99 said:**
> I tried using [this page]("http://www.ubuntuforums.org/showthread.php?t=49714&highlight=X1150.") to install my Lexmark printer, but it didn't work. The Z600 driver came up when I was trying to set up the printer, but the printer did nothing. Does anyone know how to fix this?

Output of ./z600

```
./z600: error while loading shared libraries: liblexprinter.so.0: cannot open shared object file: No such file or directory

```

Don't worry. I fixed it :)
Hey! I'm having the same problem! how did you fix it? I keep getting permission denied when I try to run 'sudo ldconfig' plus where the guide says put the files in their right place where does he mean? I'm new to Linux and as you may be able to tell a little lost. Please help!
I extract the two packages with the tar command and then run sudo ldconfig but there is no result. I must be missing something but what it is I'm buggered if I know!

---

