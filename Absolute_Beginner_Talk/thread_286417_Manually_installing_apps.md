---
title: "Manually installing apps"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by NegativeSpace on 2006-10-27
Hi,

Can someone please tell me where to place programs -- i.e., the same place when using Synaptic or apt-get -- when installing them manually?

/usr/bin ?

Regards.

---

### Post by po0f on 2006-10-27
NegativeSpace,

If you manually install stuff not using your package manager (apt in this case), it will probably lead to headaches down the road (a program overwriting another's libraries/binaries).  Use /usr/local for manually compiling and installing stuff not already in Ubuntu's repositories.

What package are you wanting to install, anyway?  And if you really want to do it there is a way.

---

### Post by bsussman on 2006-10-27
While /usr/bin is not a bad choice, there is a standard - see [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/) for more info.

Depending on what it is, /opt or /usr/local might be a more appropriate place.

How standard do you want to be?  Who needs to know where stuff is?

---

### Post by NegativeSpace on 2006-10-27
Hi po0f,

I'm trying to install IntelliJ IDEA -- a Java IDE.

Unfortunately it isn't available in any repository, so it's manual install only.

While I'm at it, I installed Sun's JDK via automatix, would I be correct in adding /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/bin to JDK_HOME as an environment variable?

bsussman, I am the only person who uses this machine, so I am the only person who needs to use it.

Regards.

---

### Post by po0f on 2006-10-27
NegativeSpace,

I cannot answer the Java question as I don't use it.

To install it in /usr, when you go to run ./configure, just pass it --prefix=/usr (it usually defaults to /usr/local):
```
$ ./configure --prefix=/usr
$ make
$ sudo make install
```

Someone will probably chime in and say you should use checkinstall instead of install, ask them for details.  :)

---

### Post by NegativeSpace on 2006-10-27
Okay, po0f, I will try that.

Thanks for your help.

---

