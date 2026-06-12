---
title: "Problem updating software"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by zaxer on 2005-10-09
Hi guys Im having problems when doing software updating. There is 4 apps that dont download. I got this error. Can you please help me? THANKS.

```
W: Falló al obtener http://security.ubuntu.com/ubuntu/pool/main/m/mozilla/libnspr4_1.7.10-0ubuntu05.04.1_i386.deb
  404 Not Found [IP: 82.211.81.182 80]

W: Falló al obtener http://security.ubuntu.com/ubuntu/pool/main/m/mozilla/libnss3_1.7.10-0ubuntu05.04.1_i386.deb
  404 Not Found [IP: 82.211.81.182 80]

W: Falló al obtener http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-image-2.6.10-5-386_2.6.10-34.5_i386.deb
  404 Not Found [IP: 82.211.81.182 80]

W: Falló al obtener http://security.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.51-2ubuntu1.1_i386.deb
  404 Not Found [IP: 82.211.81.182 80]

```

---

### Post by heimo on 2005-10-09
If you're using Synaptic, hit Reload button and try again. Or you could try to run this on terminal (hit alt+F2 and type xterm to open terminal window):
```
sudo apt-get update
sudo apt-get upgrade

```

Do you still get the errors?

---

### Post by zaxer on 2005-10-09
[QUOTE=heimo]If you're using Synaptic, hit Reload button and try again. Or you could try to run this on terminal (hit alt+F2 and type xterm to open terminal window):
```
sudo apt-get update
sudo apt-get upgrade

```

Do you still get the errors?[/QUOTE]
Yes.

It tells me to try with --fix-missing. How do I type that command?

THANKS

---

### Post by mlomker on 2005-10-09
> It tells me to try with --fix-missing. How do I type that command?


If you could post your /etc/apt/sources.list file and the complete error message then that would help.

---

### Post by heimo on 2005-10-09
Some of these may help:
```
sudo apt-get install -f
sudo apt-get install --fix-missing
sudo dpkg --configure -a

```

And as mlomker says copy of your /etc/apt/sources.list would help us. :)

---

