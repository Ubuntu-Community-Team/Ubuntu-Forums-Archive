---
title: "linux headers"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by mills on 2007-04-20
i need to install linux headers for wireless but dont know which set to install

```
alex@alex-desktop:~$ sudo apt-get install linux-headers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.17-11-server-bigiron 2.6.17.1-11.37
  linux-headers-2.6.17-11-server 2.6.17.1-11.37
  linux-headers-2.6.17-11-generic 2.6.17.1-11.37
  linux-headers-2.6.17-11-386 2.6.17.1-11.37
  linux-headers-2.6.17-11 2.6.17.1-11.37
  linux-headers-2.6.17-10-server-bigiron 2.6.17.1-10.34
  linux-headers-2.6.17-10-server 2.6.17.1-10.34
  linux-headers-2.6.17-10-generic 2.6.17.1-10.34
  linux-headers-2.6.17-10-386 2.6.17.1-10.34
  linux-headers-2.6.17-10 2.6.17.1-10.34
You should explicitly select one to install.
E: Package linux-headers has no installation candidate
```


any ideas?

cheers

---

### Post by bobplano on 2007-04-20
when you boot from grub what kernel is it? that is the headers you need. i don't know exactly which one for each kernel though but you could try generic

---

### Post by Bachstelze on 2007-04-20
```
sudo apt-get install linux-headers-$(uname -r)
```

will install the headers matching your current running kernel.

---

### Post by mills on 2007-04-20
thats sorted it

much appreciated,

---

