---
title: "WinRar files and Ubuntu, how to?"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by dbonline on 2006-09-07
how do you unpack Winrar files in Linux? I cannot figure this out for the life of me, thanks in advance...

---

### Post by Omnios on 2006-09-07
thread links.
[http://ubuntuforums.org/showthread.php?t=246201&highlight=rar](http://ubuntuforums.org/showthread.php?t=246201&highlight=rar)
[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

---

### Post by jordanmthomas on 2006-09-07
Enable multiverse / universe repositories 
Install unrar
I'm pretty sure this will go ahead and set whatever archive manager you use to use it.
If not, you can run unrar from a command line and see the options for yourself.


[http://easyubuntu.freecontrib.org/]("http://easyubuntu.freecontrib.org/")
(also, you can use EasyUbuntu and it will work for sure)

**bah, too slow!**

---

### Post by arkangel on 2006-09-07
terminal: 
> sudo aptitude install unrar

---

### Post by dbonline on 2006-09-07
awsome, I cannot believe how easy it is to use Ubuntu, I LOVE IT!! thanks for the help guys :KS

---

### Post by menschtx on 2008-06-08
For a newbie like me I found this for Ubuntu - 
[http://linuxappfinder.com/package/unrar-free](http://linuxappfinder.com/package/unrar-free). We will see how it works.

---

### Post by ubuntu27 on 2008-06-08
> **menschtx said:**
> For a newbie like me I found this for Ubuntu - 
[http://linuxappfinder.com/package/unrar-free](http://linuxappfinder.com/package/unrar-free). We will see how it works.

That one is also in the repository, meaning you can instal with a simple terminal command or with Synaptic Package Manager.

```
sudo apt-get install unrar-free
```

---

