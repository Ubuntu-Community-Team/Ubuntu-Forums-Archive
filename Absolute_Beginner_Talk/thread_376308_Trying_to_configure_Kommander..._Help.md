---
title: "Trying to configure Kommander... Help?"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by ImmortalGrey on 2007-03-04
I've got Kommander-Executor downloaded to my desktop, I just need to compile it for installation, so I can run the install file for KPOPS Converter 1.51 which is a .kmdr file...

So, here's my terminal when I do this:

```
robb@robb-desktop:~/Desktop/kommander-executor-1.1devel2$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

So I head on over to 'config.log' and this is what I get that stood out:

```
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "kommander-executor-1.1devel2"
| #define VERSION "3.3.0"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2814: error: C compiler cannot create executables
See `config.log' for more details.
```

... Help please?

---

### Post by taurus on 2007-03-04
You need the build-essential package before you can build anything.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by ImmortalGrey on 2007-03-04
> **taurus said:**
> You need the build-essential package before you can build anything.

```
sudo aptitude update
sudo aptitude install build-essential
```

Alright, got that all set...  Things were running fine for a few seconds, and now I get this message:

```
Checking for X... configure:  error:  Can't find X includes.  Please check your installation and add the correct paths!
```

X?  Unfamiliar as to what to do with that message...

---

### Post by taurus on 2007-03-04
Maybe 

```
sudo aptitude install xorg-dev
```

---

### Post by ImmortalGrey on 2007-03-04
> **taurus said:**
> Maybe 

```
sudo aptitude install xorg-dev
```

Got it!  Thanks so much. :)

---

