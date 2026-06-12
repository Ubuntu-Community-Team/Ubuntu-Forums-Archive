---
title: "Error installing from source."
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by HIGHLIFE on 2007-01-08
I was trying to install Videotrans for Qdvdauthor but when I do ./configure I get this error:

configure:2822: error: /bin/bash './configure' failed for src

Does anyone how I could fix this?

---

### Post by teaker1s on 2007-01-09
user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

cd into your folder then 

user@ubuntu:~/nameofyourfolder$ make distclean

may or may not need  " ./configure "

user@ubuntu:~/nameofyourfolder$ make
user@ubuntu:~/nameofyourfolder$ sudo make install

---

### Post by HIGHLIFE on 2007-01-09
I already had the correct linux-headers installed, and when I went to the directory with the source I was trying to install and used "make distclean" I got a [clean] Error 1.](*,)

---

### Post by HIGHLIFE on 2007-01-10
No One:-k ?

---

