---
title: "Issues with compiling. GCC, etc."
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by shibasu on 2006-01-23
Hi, i'm rather new to *nix. 

My issues is this
> 
diux@configure:~/xmms-1.2.10$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for prefix by checking for xmms... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.


Now, from my previous expierence with Ubuntu, it came with the GCC compiler, so i'm not sure.

When I try to install the GCC compiler it tells me 

"Cannot compile in source folder" If anyone knows how to compile GCC properly that could lend me some info, if that's the problem, i'd appreciate it.

Any ideas on how to make this run?

---

### Post by dueY on 2006-01-23
```
sudo apt-get install build-essential
```

---

### Post by cwaldbieser on 2006-01-23
[QUOTE=shibasu]Hi, i'm rather new to *nix. 

My issues is this


Now, from my previous expierence with Ubuntu, it came with the GCC compiler, so i'm not sure.

When I try to install the GCC compiler it tells me 

"Cannot compile in source folder" If anyone knows how to compile GCC properly that could lend me some info, if that's the problem, i'd appreciate it.

Any ideas on how to make this run?[/QUOTE]

Try installing your compiler toolchain with
```

$ sudo apt-get build-essentials

```
Take a look here for different ways to install software:
[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

---

### Post by shibasu on 2006-01-23
Thanks for the help.

I'll try it out now and edit my post accordingly

Edit: 

diux@configure:~$ sudo apt-get build-essentials
E: Invalid operation build-essentials
diux@configure:~$


Did apt-get update before hand as well.

I blame my stupidity on fatigue!

Thanks for all your help, i'm up and running. Although a bit ashamed:|

Any ideas?

---

### Post by hillbilly on 2006-01-23
Do > sudo apt-get install build-essentials

---

### Post by cwaldbieser on 2006-01-24
My bad.  I forgot the install.  Also, the package is "build-essential" not "build-essentials".

---

