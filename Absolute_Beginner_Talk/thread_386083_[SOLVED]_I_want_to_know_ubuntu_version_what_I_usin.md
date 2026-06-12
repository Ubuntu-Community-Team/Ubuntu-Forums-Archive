---
title: "[SOLVED] I want to know ubuntu version what I using now."
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Masoris on 2007-03-16
I want to know ubuntu version what I using now?
Am I using ubuntu Dapper or Edgy now?
x86 version or amd64 version?

How can I know this?

---

### Post by Adam_GUI on 2007-03-16
In a terminal, type:
```
uname -a
```

---

### Post by KLineD on 2007-03-16
Go to System > About Ubuntu

In there you'll find something like this:

Thank you for your interest in Ubuntu 6.10 - the Edgy Eft - released in October 2006.

And now you know what version you are using.

---

### Post by AtrejuT on 2007-03-16
the first thing that comes to my mind is having a look at your
/etc/apt/sources.list
file and see which repositories it lists...

atreju

---

### Post by Najand on 2007-03-16
Open Firefox and go to:
[file:///usr/share/ubuntu-artwork/home/index.html]("file:///usr/share/ubuntu-artwork/home/index.html")
For  finding your architecture open a terminal and run:
```

uname -m

```

---

### Post by Masoris on 2007-03-16
```

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux
ubuntu@ubuntu:~$ uname -m
x86_64

```
Does 'x86_64' means amd64 version?


x86 = x86
amd64 = x86_64
Power_PC = ???

---

### Post by Najand on 2007-03-16
AMD64 is x86_64, check:
[http://en.wikipedia.org/w/index.php?title=AMD64&redirect=no]("http://en.wikipedia.org/w/index.php?title=AMD64&redirect=no")
Also 
PowerPC= ppc

---

### Post by Masoris on 2007-03-16
Okay, I see thanks :)

---

### Post by Najand on 2007-03-16
However considering your Kernel Version, you probably have Edgy Eft installed.

---

### Post by bapoumba on 2007-03-17
```
lsb_release -cd
```

---

