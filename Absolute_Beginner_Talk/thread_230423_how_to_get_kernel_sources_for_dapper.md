---
title: "how to get kernel sources for dapper?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by wildseven on 2006-08-05
hello, i am trying to make make install a patch driver for madwifi but i get this error:
```
/bin/sh: line 0: cd: /lib/modules/2.6.15-26-386/build: No such file or directoryMakefile.inc:89: *** /lib/modules/2.6.15-26-386/build is missing, please set KERNELPATH.  Stop.
```

i talked to someone on another forum and they said i need my kernel sources. i am not sure how to get them or what they are. please help if possible.
thank you

---

### Post by pdub on 2006-08-05
assuming you have kernel version 2.6.15-26-386 (you can find this by typing uname -r)

sudo apt-get install linux-headers-2.6.15-26-386 

sudo rm /usr/src/linux

sudo ln -s /usr/src/linux-headers-2.6.15-26-386 /usr/src/linux

---

