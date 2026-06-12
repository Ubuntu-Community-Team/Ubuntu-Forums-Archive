---
title: "ET Error"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2007-01-27
I get the following error when trying to install enemy territory, what is the problem?

/root/.setup10939: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1


Thanks

---

### Post by trill on 2007-01-27
I had this happen to.

```
sudo apt-get install libgtk1.2
```

and it was fine

---

