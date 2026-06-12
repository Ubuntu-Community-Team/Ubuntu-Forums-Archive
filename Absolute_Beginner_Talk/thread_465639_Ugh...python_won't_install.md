---
title: "Ugh...python won't install"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by prophet001 on 2007-06-05
Ok so for some reason the python package installer is broken, so I downloaded python and tried to install it manually. I'm using python-2.5.1 and doing the standard ./configure, make, make install on feisty. ./configure runs fine, and it compiles alright, but when i run make install, I get this garbage:

ben@ben-laptop:~/Desktop/Python-2.5.1$ make install
/usr/bin/install -c python /usr/local/bin/python2.5
/usr/bin/install: cannot create regular file `/usr/local/bin/python2.5': Permission denied
make: *** [altbininstall] Error 1
ben@ben-laptop:~/Desktop/Python-2.5.1$ 

I will admit, I know enough to get myself in trouble, but I'm still a noob. HALP!!!

---

### Post by maob on 2007-06-05
Try running it with sudo..

---

### Post by ceeg on 2007-06-05
```

./configure
make
sudo make install

```

By the way, the python package has worked fine for me in the past. What exactly is wrong with it?

---

