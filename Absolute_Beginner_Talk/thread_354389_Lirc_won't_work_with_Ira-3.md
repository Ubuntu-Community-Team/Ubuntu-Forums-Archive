---
title: "Lirc won't work with Ira-3"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Shawn Dineley on 2007-02-05
Hello 

      I'm trying to install Lirc 0.8.0 on my dapper system. I've tried about 5 How to's and nothing seems to work. At one point I got the status led to come on, but not sure how? I've been working on this all day (searching the forums and google). And I know it work (at least in Xp). Here's a link to the website for the receiver.
[http://www.home-electro.com/ira3.php?osCsid=0632b5a6d493f87f792a3fa16a539bf9&osCsid=0632b5a6d493f87f792a3fa16a539bf9](http://www.home-electro.com/ira3.php?osCsid=0632b5a6d493f87f792a3fa16a539bf9&osCsid=0632b5a6d493f87f792a3fa16a539bf9)

Please help I'm stuck???

---

### Post by shareMenaPeace on 2007-02-05
Did you checked this guide too?
[https://help.ubuntu.com/community/LircSupport?highlight=%28Lirc%29](https://help.ubuntu.com/community/LircSupport?highlight=%28Lirc%29)

---

### Post by Shawn Dineley on 2007-02-05
Nope, but give me a couple min and I'll try it??

---

### Post by shareMenaPeace on 2007-02-05
> **Shawn Dineley said:**
> Nope, but give me a couple min and I'll try it??
Of course :)

---

### Post by Shawn Dineley on 2007-02-05
Ok I got to the command ":/usr/src/linux$ sudo make modules" and it give me an error.

shawn@shawn-desktop:/usr/src/linux$ sudo make modules
  CHK     include/linux/version.h
  SPLIT   include/linux/autoconf.h -> include/config/*
  CC      scripts/mod/empty.o
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
make[1]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make: *** [arch/i386/kernel] Error 2

---

