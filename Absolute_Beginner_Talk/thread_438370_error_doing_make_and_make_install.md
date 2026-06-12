---
title: "error doing make and make install"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-05-09
** make**

make -C driver
make[1]: Entering directory `/home/ohg/Desktop/ndiswrapper-1.43/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/ohg/Desktop/ndiswrapper-1.43/driver'
make: *** [all] Error 2

** sudo make install**

Password:
make -C driver install
make[1]: Entering directory `/home/ohg/Desktop/ndiswrapper-1.43/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/ohg/Desktop/ndiswrapper-1.43/driver'
make: *** [install] Error 2
ohg@ohg-laptop:~/Desktop/ndiswrapper-1.43$


anyone knows what's wrong?

---

### Post by jargoman on 2007-05-09
on default install this should work

$ sudo apt-get update
$ sudo apt-get install build-essential

$ make
$ sudo make install

copy and paste if you wish. worked for me on fresh install

note you need ethernet connect for the first 2 commands

---

### Post by Cypher on 2007-05-09
You need the Kernel sources to build a Kernel loadable module.

Also, as a general rule of thumb, NEVER do a "sudo make install" if there were ANY errors during a "make". It just isn't a safe thing to do.

---

### Post by Pulka on 2007-05-09
> **jargoman said:**
> on default install this should work

$ sudo apt-get update
$ sudo apt-get install build-essential

$ make
$ sudo make install

copy and paste if you wish. worked for me on fresh install

note you need ethernet connect for the first 2 commands

yeah, i have a fresh installation of ubuntu, and i tried to do it before installing buil-essential. but now i already installed and still gives me the error

---

### Post by Bachstelze on 2007-05-09
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

then make clean and try to make again, nothing else should be needed for ndiswrapper.

---

### Post by Pulka on 2007-05-09
> **Cypher said:**
> You need the Kernel sources to build a Kernel loadable module.



sorry, but what does this mean? :)

---

### Post by jargoman on 2007-05-09
note that I edited my last post because I forgot the sudo in front of make install. also if your worried about past install attempts lingering around

$ sudo make uninstall

---

### Post by Pulka on 2007-05-09
> **HymnToLife said:**
> ```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

then make clean and try to make again, nothing else should be needed for ndiswrapper.



errr....i don't have access to internet. how can i get the headers?

---

### Post by Bachstelze on 2007-05-09
They're on your Ubuntu CD just like build-essential.

---

### Post by Cypher on 2007-05-09
How are you talking to us without Internet access?? :)

---

### Post by Pulka on 2007-05-09
worked. Thank you all. Sorry for my newbiness

---

### Post by jargoman on 2007-05-09
It's asking for the linux source code but as HymnToLife pointed out you only need linux headers. His command should work. Odd because I had my headers installed out the box? Your source (or headers) should be located in /usr/src

$ cd /usr/src
$ ls

you might need to extract it if it's in .tar.gz or tar.bz form

$ sudo tar -xvf linux-headers ( then just hit <tab> for auto complete)

you can look around synaptic manager for your headers also. you need the right headers to correspond with your kernel. 

$ `uname -r`
will tell you what kernel your running

hence 
$ sudo apt-get install linux-headers-$(uname -r)

---

### Post by Bachstelze on 2007-05-09
> **jargoman said:**
> 
$ `uname -r`
will tell you what kernel your running


Wrong.

```
$ uname -r
```

or

```
$ echo `uname -r`
```

will show the kernel version.

```
$ `uname -r`
```

will generally throw a "command not found" error.

---

### Post by Pulka on 2007-05-10
> **Cypher said:**
> How are you talking to us without Internet access?? :)

having two computers. One wireless laptop and one desktop.

---

### Post by Pulka on 2007-05-10
Thank you HymnToLife for your help. It´s working now

---

