---
title: "[SOLVED] tcpreplay and libopts.so.24"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by joot211 on 2007-09-03
I trying to run tcpreplay. it seems to be looking for libopts.so.25

 error while loading shared libraries: libopts.so.25: cannot open shared object file: No such file or directory

...But I installed libopts.so.25 and it still can´t find it

any suggestions?

---

### Post by joot211 on 2007-09-03
I tried reinstalation of both tcpreplay and libopts25. same damn result


tcpreplay: error while loading shared libraries: libopts.so.25: cannot open shared object file: No such file or directory

---

### Post by Perfect Storm on 2007-09-03
Try this;
```
sudo ln -s /usr/lib/libopts.so.24 /usr/lib/libopts.so.25
```

---

### Post by joot211 on 2007-09-03
thank you. the symlink worked
 :)

---

