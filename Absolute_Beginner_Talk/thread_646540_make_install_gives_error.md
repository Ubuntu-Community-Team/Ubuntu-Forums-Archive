---
title: "make install gives error"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by saurabh kakkar on 2007-12-21
whenever i try to do make install on any package it gives me error like this .i m using ubuntu 7.04

```

saurabh@ubuntu:~$ cd ~/Desktop
saurabh@ubuntu:~/Desktop$ cd cabextract-1.2
saurabh@ubuntu:~/Desktop/cabextract-1.2$ make install
make[1]: Entering directory `/home/saurabh/Desktop/cabextract-1.2'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'cabextract' '/usr/local/bin/cabextract'
/usr/bin/install: cannot create regular file `/usr/local/bin/cabextract': Permission denied
make[1]: *** [install-binPROGRAMS] Error 1
make[1]: Leaving directory `/home/saurabh/Desktop/cabextract-1.2'
make: *** [install-am] Error 2
saurabh@ubuntu:~/Desktop/cabextract-1.2$ 

```

i have installed essentials by
```

sudo apt-get install build-essential linux-headers-$(uname -r)

```

---

### Post by taurus on 2007-12-21
```
**sudo** make install
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

