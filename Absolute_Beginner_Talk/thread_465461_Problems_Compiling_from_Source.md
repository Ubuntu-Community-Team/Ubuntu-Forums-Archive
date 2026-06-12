---
title: "Problems Compiling from Source"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Hoso001 on 2007-06-05
I am trying to install some software from source on a brand new install of feisty fawn. I am trying to compile this software and i am getting errors, it is saying that my gcc dosen't support compiling executables. I would love to be able to compile these programs from source, can anyone point me in the right direction to fix this?

Thanks

David

P.S. Here is my Error Log


```

david@david-laptop:~/Desktop/wine-0.9.38$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

---

### Post by taurus on 2007-06-05
You need the build-essential package before you can compile anything.

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by jvc26 on 2007-06-05
Have you installed the build-essential package?
```

sudo apt-get install build-essential

```
That may well solve your issue,
Il

---

