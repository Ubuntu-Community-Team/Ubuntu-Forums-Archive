---
title: "Understanding Synaptic"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by NT4.0 on 2007-02-02
I had to reinstall my Ubuntu 6.06 system and I had necessary software on a DVD. During my first Ubuntu experience I downloaded and installed packages by hand, but when I learned about dependencies I realized a package manager would be more convenient. I used Synaptic and after it downloaded a package with all dependencies I picked them up in /var/cache/apt and copied to my software directory. Today I reinstalled my system and had to renew its database which included the Universe repository list. I haven't yet figured out where its database files are, I thought they were /var/cache/apt/*pkgcache.bin, maybe not. But the problem is, when I tried to use Synaptic to install my packages from the DVD fast ("Add Downloaded Packages" option), it used the new database and asked me for the NEW dependencies (some packages were updated and probably required new dependencies). I have a very slow connection (dial-up) and can't afford that, plus I would like to have my software on my media which would install fine after system reinstall, now I am thinking how I can save Synaptic's database to give it the "old" one to be able to install the packages. apt-get does not always help (or I may have to learn more), and sometimes I have the catch 22 with two packages. When I used to have Windows, it was simple, I just kept the software and installed it whenever I wanted, now here it all seems more interactive, but I'd rather have it the old way. Any help would be great.

---

### Post by deadgobby on 2007-02-02
You could try the Apt and on CD.
[https://wiki.ubuntu.com/APTonCD?highlight=%28cd%29](https://wiki.ubuntu.com/APTonCD?highlight=%28cd%29)
Here is some links
[http://ubuntuclips.org/](http://ubuntuclips.org/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

GObby

---

### Post by NT4.0 on 2007-02-05
Thank you, it seems nice, though I can't install aptoncd. I downloaded the *.deb package it required python-dbus. I found that it was for Debian and not Ubuntu but I downloaded it and tried to install. It said "conflict with python2.4-dbus" package. So I don't see any way to install aptoncd; besides it is not present in the repositories, Any advice?

---

