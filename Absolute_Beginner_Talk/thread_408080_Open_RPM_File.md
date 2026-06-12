---
title: "Open RPM File"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by gsk320 on 2007-04-12
I try to open an RPM file using Archive Manager, but it says Archive Type not supported. Whats wrong?

---

### Post by tonyr1988 on 2007-04-12
RPM is called RedHat Package Manager. It's an alternative to Ubuntu's *.deb files.

Try this:

Applications >> Accessories >> Terminal

> sudo apt-get install alien

After that, try (still in Terminal):

> alien {path_to_rpm_file}

For example, if my_file.rpm is on your Desktop, try:

> alien ~/Desktop/my_file.rpm

---

### Post by Raptor45 on 2007-04-12
RPMs are not used by Ubuntu, and so you will not be able to use it. A program called alien is capable of converting RPMs into DEBs, which can be installed. I suggest you try it out.

---

### Post by Malakia on 2007-04-12
You need to change it into a .deb file using alien.

```
sudo aptitude install alien

sudo alien -d package.rpm (-d for Debian package)
```

Here is the link to where I found it, a wealth of information.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_.26_use_.rpm_to_.deb_Converter_.28Alien.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_.26_use_.rpm_to_.deb_Converter_.28Alien.29")

---

### Post by Maestro23 on 2007-04-12
Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

---

### Post by gsk320 on 2007-04-12
thanks everyone it works now

---

