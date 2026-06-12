---
title: "Nerolinux Error"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by darkNiGHTS on 2007-10-21
Whenever I try running NeroLinux, I get an error about a .so file that is in the right place, but the program can't seem to find it:

```
nero: error while loading shared libraries: libNeroAPI.so: cannot open shared object file: No such file or directory
```

I am running Ubuntu 7.10 x64 if that is useful.  I don't know what other  information to give so if you need to ask any more questions, ask away.

Please help, I need to get this working!  Otherwise I will have to boot into Windows.

Thanks.

---

### Post by JangMunho on 2007-11-30
I'm now ready to help you solve all the problem. Try the following commands in a terminal:
```

sudo ln -s /usr/lib/libNero*.so /usr/lib32/
sudo ln -s /usr/lib/libNewTrf.so /usr/lib32/
sudo ln -s /usr/lib/libCDCopy.so /usr/lib32/

```

Now, you can start nero and enjoy it...

---

