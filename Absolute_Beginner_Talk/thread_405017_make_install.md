---
title: "make install"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by tuannguyen on 2007-04-09
hello everyone,

I want install a source packet in ubuntu, I used "make" command, that is ok (no error). Now i use command "make install" to install this source but can't. I find GNU install in Synaptic but can't find it. Anyone can tell me, what happen and how can i solve it

thanks in advance,
T,

---

### Post by jakev383 on 2007-04-09
> **tuannguyen said:**
> hello everyone,

I want install a source packet in ubuntu, I used "make" command, that is ok (no error). Now i use command "make install" to install this source but can't. I find GNU install in Synaptic but can't find it. Anyone can tell me, what happen and how can i solve it

thanks in advance,
T,
Do you have the build tools installed? (apt-get install build-essential) Then try running it again. There's also usually a configure script to be run. Otherwise, it would be helpful to know exactly what is not working - does it give an error?

---

### Post by tuannguyen on 2007-04-09
> **jakev383 said:**
> Do you have the build tools installed? (apt-get install build-essential) Then try running it again. There's also usually a configure script to be run. Otherwise, it would be helpful to know exactly what is not working - does it give an error?

thanks jake,

I've just used: apt-get install build-essential but I got folow error:

tuandat@ubuntu:~$ sudo apt-get install build-essential
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what does it mean?

when I done "make install", there is no error, simple don't working (don't install)
T.

---

### Post by teaker1s on 2007-04-09
that error either normally means Synaptic or update icon running

---

### Post by tuannguyen on 2007-04-09
> **jakev383 said:**
> Do you have the build tools installed? (apt-get install build-essential) Then try running it again. There's also usually a configure script to be run. Otherwise, it would be helpful to know exactly what is not working - does it give an error?

I've installed build tools, that is ok. but "make install" don't working and there is no error.

tuandat@ubuntu:~/sip_router$ make prefix=/usr/local install
tuandat@ubuntu:~/sip_router$ make prefix=/usr/local install

what must i do now?

T.

---

### Post by seshomaru samma on 2007-04-09
what about:
```
checkinstall
```
?

---

