---
title: "Where to download Linux Kernel"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-01-15
Hi where would I find the latest version of the kernel?? Thanks :)

---

### Post by pay on 2007-01-15
[www.kernel.org](www.kernel.org)

---

### Post by nite owl on 2007-01-15
Thanks pay...

---

### Post by nite owl on 2007-01-15
Actually I can't seem to find a specific binary version for my i686 architecture??? and what is a .bz2 file I was hoping for a .deb?? would dpkg -i still work?? Like on the redhat website for redhat users you have a wide variety of Kernels for the different architectures(i386, i586, i686 etc.) also has versions such as bigmem(machines with 4gb's or more) and smp(multiple processors). Is there an equivalent???

---

### Post by Henry Rayker on 2007-01-15
.tar.bz2 is a compressed source archive. Typically, the "latest" is going to be source only...you could compile it, but it could present trouble. If you're worried about that, stick to the kernel version in the repos.

---

### Post by el-sio on 2007-01-15
I don't know what you are trying to do, but either you compile the whole kernel from the source (and tune it to your specific system details), or you simply install the packages related to the kernel (like linux-headers...) from Synaptics.

In the first case, extract the compressed source archive you got using file roller  by simply right-clicking and extract, or using the command line
```
tar xjf file.tar.bz2
``` 
then go into the created directory and try sudo 
```

sudo ./configure
sudo make
sudo make install
```

In the second case, well just look for linux in synaptics...

---

### Post by pay on 2007-01-15
> **el-sio said:**
> ```
tar xjf file.tar.bz2
``` 
then go into the created directory and try sudo 
```

sudo ./configure
sudo make
sudo make install
```That would be a generic way to compile source code but for a Linux kernel it would be alittle different. Follow this guide and it will explain how to make a debian package of the linux kernel (it's not that hard). [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

