---
title: "How to compile Netcat in Ubuntu Linux?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by livefordirty on 2006-08-02
How to compile Netcat in Ubuntu Linux6.06?
when i compile netcat according to Makefile:

" make -e $(ALL) $(MFLAGS) XFLAGS='-DLINUX' STATIC=-static"

the ubuntu said:
bash: ALL: command not found
bash: MFLAGS: command not found
Usage:  make  <systype>  [options]

what's wrong with it?
How to solve this problem?


Thanks!

---

### Post by shanepardue on 2006-08-02
i believe the best route to be install the package checkinstall then type the following

```
./configure
sudo checkinstall
```

checkinstall will do everything for you and allow for a much better removal system. check it out!

---

### Post by livefordirty on 2006-08-02
./configure doesnt work in my ubuntu!

The ubuntu said:
bash: ./configure: No such file or directory

what's wrong with it?

Thanks

---

### Post by hw-tph on 2006-08-02
What's wrong with getting it from the main repository? **sudo apt-get install netcat** should do it.

If you still want to build it from source, untar the source (netcat-0.7.1.tar.bz2 (or .gz)) and enter the newly created directory. From there you can run the configure script and build it.


Håkan

---

