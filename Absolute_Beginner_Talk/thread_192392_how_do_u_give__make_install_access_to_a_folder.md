---
title: "how do u give  make install access to a folder?"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-08
trying to install an app with the following command  make install but i get an error that it doesn't have permission to creat a folder.. Here is a copy of the ouput

john@ubuntu:~/Desktop/gnump3d-2.9.8$ make install
install -d /etc/gnump3d
install: cannot create directory `/etc/gnump3d': Permission denied
make: *** [install] Error 1

---

### Post by meng on 2006-06-08
sudo make install
is what you want.

---

### Post by taurus on 2006-06-08
```

sudo make install
(use the same password that you use to log in to your account...)

```

---

### Post by xXx 0wn3d xXx on 2006-06-08
[QUOTE=lime4x4]trying to install an app with the following command  make install but i get an error that it doesn't have permission to creat a folder.. Here is a copy of the ouput

john@ubuntu:~/Desktop/gnump3d-2.9.8$ make install
install -d /etc/gnump3d
install: cannot create directory `/etc/gnump3d': Permission denied
make: *** [install] Error 1[/QUOTE]
Use:
> sudo make install

---

### Post by meng on 2006-06-08
Yup the verdict is unanimous!

---

### Post by lime4x4 on 2006-06-08
thanks and it was somehting so simple....lol

---

### Post by taurus on 2006-06-08
Just remember, everytime you need to write/modify system's directories, you need to be root so the sudo before the command is required.

---

