---
title: "Windows *.exe"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by KeeperMustDie on 2007-03-19
Hi, I totally new in Ubuntu and Linux itself and I want to know: is there any way to run Windows executables on Ubuntu. For example I have Borland C++ Builder. Do I need to get special Builder for Linux or I cant somehow run existing one?

---

### Post by Lord Illidan on 2007-03-19
Hi, and welcome to the forums.

In answer to your question, yes you can run exes under Linux with wine.

[www.winehq.org]("http://www.winehq.org")

It is in the Ubuntu Repositories.

Type this in a terminal (Applications -> Accessories -> Terminal)
```
sudo apt-get install wine
```Note, if that command does not work, please type in the same terminal.
```
gedit /etc/apt/sources.list
```This will open a text file, copy and paste the whole thing here.

Now, regarding C++ builder. I don't know if it can run under Wine or not, but there are many c++ IDEs for Linux. Are you interested in GUI programming or CLI?

EDIT : Also, please post any issues, problems here. Don't be put off, we were all new once.

---

### Post by LanDan on 2007-03-19
there are several options

wine allows you to run several windows programs (but probably not borland)

vmware allows you to run a complete windows operating system within linux

and offcourse option number three, try some of the tons of development software for linux

[http://www.intel.com/software/products/compilers/](http://www.intel.com/software/products/compilers/)
[http://nl.wikipedia.org/wiki/Dev-C_Plus_Plus](http://nl.wikipedia.org/wiki/Dev-C_Plus_Plus)
[http://nl.wikipedia.org/w/index.php?title=Code::Blocks&action=edit](http://nl.wikipedia.org/w/index.php?title=Code::Blocks&action=edit)
[http://nl.wikipedia.org/wiki/Eclipse_%28software%29](http://nl.wikipedia.org/wiki/Eclipse_%28software%29)
[http://nl.wikipedia.org/wiki/KDevelop](http://nl.wikipedia.org/wiki/KDevelop)

---

### Post by mcduck on 2007-03-19
You can run some windows apps using Wine, but if you just want to compile C++ files install the build-essential package, it contains everything you need for compiling stuff :)

---

### Post by kinematic on 2007-03-19
you can get some windows executables to run on gnu/linux using wine wich is an emulator of the windows api but if you're looking for a better operating system just to run windows exe's then gnu/linux isn't for you.
it's a totally different operating system and has applications that are better or as good as those you can find for windows.
one of the apps is the gnu c++ compiler wich you can find in the ubuntu repository....just open synaptic and search for g++ and it will show up.

---

### Post by KeeperMustDie on 2007-03-19
Thanks all for the help. I suppose I will dl vmware because i have windows in other disk also i hope that wine will work. Also Lord Illidan I see you are WC3 player. I like this game too :) i hope WC3 works with wine. Thanks again all.

---

### Post by Lord Illidan on 2007-03-19
> **KeeperMustDie said:**
> Thanks all for the help. I suppose I will dl vmware because i have windows in other disk also i hope that wine will work. Also Lord Illidan I see you are WC3 player. I like this game too :) i hope WC3 works with wine. Thanks again all.

Yes, it does..

---

