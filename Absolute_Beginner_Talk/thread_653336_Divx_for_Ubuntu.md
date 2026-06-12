---
title: "Divx for Ubuntu?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by peterhuang913 on 2007-12-29
How anyone know how to get the Divx codec on Ubuntu. I've read over other threads, Dled the package, ran install and got this:
```

Proceeding with installation
unzip:  cannot find or open contents.dat, contents.dat.zip or contents.dat.ZIP.
cp: cannot stat `/tmp/.divx/lib/*.so': No such file or directory
mkdir: cannot create directory `/usr/local/include/divx': File exists
cp: cannot stat `/tmp/.divx/include/*': No such file or directory
chown: cannot access `/usr/local/lib/libdivx.so': No such file or directory
chmod: cannot access `/usr/local/lib/libdivx.so': No such file or directory
chown: changing ownership of `/usr/local/lib/libdivx.so.0': No such file or directory

```

---

### Post by jken146 on 2007-12-29
I've never had a problem with divX in Ubuntu.  I use VLC -- it seems to play everything.  Try installing ubuntu-restricted-extras.

---

### Post by JillSwift on 2007-12-29
Easiest way is out of the repositories:```
[SIZE=-1]sudo apt-get install ubuntu-restricted-extras[/SIZE]
```

---

### Post by peterhuang913 on 2007-12-29
> **JillSwift said:**
> Easiest way is out of the repositories:```
[SIZE=-1]sudo apt-get install ubuntu-restricted-extras[/SIZE]
```

Thanks guys, restricted-extras works great.

---

