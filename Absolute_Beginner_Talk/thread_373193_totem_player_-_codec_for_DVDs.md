---
title: "totem player - codec for DVDs?"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by stuart@gib.co.za on 2007-03-01
how do i update the codec on ubuntu 6.10 edgy so that i can watch dvds?

---

### Post by scxtt on 2007-03-01
install the following packages:
```
[font=courier]
:> aptitude search libdvd
Password:
i   libdvdcss2     - a portable abstraction library for DVD decryption
i   libdvdnav4     - The DVD navigation library
i   libdvdplay0    - portable abstraction library for DVD menus support
i   libdvdread3    - Simple foundation for reading DVDs[/font]
```
then run **sudo usr/share/doc/libdvdread3/examples/install-css.sh** ... this worked for me w/ dapper, should be the same for edgy ... i use kaffeine to watch all video ...

---

### Post by STREETURCHINE on 2007-03-01
you could install automatix

[http://www.getautomatix.com/](http://www.getautomatix.com/)

but start a new thread this is marked as resolved no one will look at it

---

### Post by aysiu on 2007-03-01
Add the correct repositories:
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

and then ```
sudo apt-get update
sudo apt-get install libdvdcss2
```

---

### Post by aysiu on 2007-03-01
> **STREETURCHINE said:**
> 
but start a new thread this is marked as resolved no one will look at it I've moved it to a new thread.

---

