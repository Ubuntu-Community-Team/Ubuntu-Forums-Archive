---
title: "where can i find gcc"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by ItsAmazazazing on 2007-08-10
Ive been looking for gcc all morning, but havent been able to find it for download in a simple format. Most of the pages are giant directories with several folders for several versions and Im getting lost because I don't know what all I need in order to have it working. Is there a website that I can go to that will have everything I need and keep it simple to download?

---

### Post by Ek0nomik on 2007-08-10
> **ItsAmazazazing said:**
> Ive been looking for gcc all morning, but havent been able to find it for download in a simple format. Most of the pages are giant directories with several folders for several versions and Im getting lost because I don't know what all I need in order to have it working. Is there a website that I can go to that will have everything I need and keep it simple to download?

Accessories/Terminal

```
sudo aptitude search gcc
```

```
p   colorgcc                        - Colorizer for GCC warning/error messages
i   gcc                             - The GNU C compiler
p   gcc-2.95                        - The GNU C compiler
p   gcc-2.95-doc                    - Documentation for the GNU compilers (gcc,
p   gcc-3.3                         - The GNU C compiler
i   gcc-3.3-base                    - The GNU Compiler Collection (base package)
p   gcc-3.3-doc                     - Documentation for the GNU compilers (gcc,
p   gcc-3.4                         - The GNU C compiler
p   gcc-3.4-base                    - The GNU Compiler Collection (base package)
p   gcc-3.4-doc                     - Documentation for the GNU compilers (gcc,
p   gcc-4.0-locales                 - The GNU C compiler (native language suppor
i   gcc-4.1                         - The GNU C compiler
i   gcc-4.1-base                    - The GNU Compiler Collection (base package)
p   gcc-4.1-doc                     - Documentation for the GNU compilers (gcc,
p   gcc-4.1-locales                 - The GNU C compiler (native language suppor
p   gcc-4.1-source                  - Source of the GNU Compiler Collection
p   gcc-avr                         - The GNU C compiler (cross compiler for avr
p   gcc-doc                         - Documentation for the GNU C compilers (gcc
v   gcc-docs                        -
p   gcc-h8300-hms                   - The GNU C compiler (cross compiler for h83
p   gcc-m68hc1x                     - GNU C compiler for the Motorola 68HC11/12
p   gcc-snapshot                    - A SNAPSHOT of the GNU Compiler Collection
p   gcc272                          - The GNU C compiler.
p   gcc272-docs                     - Documentation for the gcc compiler (gcc272
p   gccxml                          - XML output extension to GCC
p   lib64gcc1                       - GCC support library (64bit)
i   libgcc1                         - GCC support library
p   pocketpc-gcc                    - The GNU C compiler for Pocket PC
```

---

### Post by Hospadar on 2007-08-10
you are going to want to install build-essential from the repositories.

in a terminal:
```
sudo apt-get install build-essential
```This has all the tools you need to build c and c++ programs; gcc, g++, make, etc.

Edit: this is all command line, if you want IDE stuff, also consider installing kdevelop, eclipse cdt, or anjuta.

---

### Post by SOULRiDER on 2007-08-10
If youre planning on creating deb packages i suggest:
```
sudo aptitude install checkinstall
```

---

### Post by ridgeland on 2007-08-10
Try synaptics for packages before searching all over the web.
Menu -> System -> Administration
gcc is an option there and you'll get the latest supported version with a very easy install.
I see I have "build-essential" installed too.  Maybe try it too and see what dependancies it brings with it.

---

### Post by Hospadar on 2007-08-10
build-essential is actually just an empty package that depends on the latest version of all the build tools, so when you install it it will install all the tools you need.

---

### Post by ItsAmazazazing on 2007-08-10
Sweet, got it. I really appreciate everyones help!

---

### Post by freebsd on 2007-08-13
but what about those wanting to install GCC without net connection, does 6.06LTS has GCC on CD ?:confused:

---

### Post by stchman on 2007-08-13
> **ItsAmazazazing said:**
> Ive been looking for gcc all morning, but havent been able to find it for download in a simple format. Most of the pages are giant directories with several folders for several versions and Im getting lost because I don't know what all I need in order to have it working. Is there a website that I can go to that will have everything I need and keep it simple to download?

gcc/g++ is installed by default in Ubuntu.  All you need to do to compile programs and drivers is the following:

sudo apt-get -y install build essential

---

### Post by Ek0nomik on 2007-08-13
> **stchman said:**
> gcc/g++ is installed by default in Ubuntu.  All you need to do to compile programs and drivers is the following:

sudo apt-get -y install build essential

He already solved this problem, and the installing of build-essential has already been posted if you look a few posts up...

> **freebsd said:**
> but what about those wanting to install GCC without net connection, does 6.06LTS has GCC on CD ?:confused:

freebsd:  I am quite certain build-essential is on the 6.06 CD.  If it isn't, you could go to the public library and put it on a USB device and run it that way.

---

### Post by LaRoza on 2007-08-13
> **Ek0nomik said:**
> He already solved this problem, and the installing of build-essential has already been posted if you look a few posts up...



freebsd:  I am quite certain build-essential is on the 6.06 CD.  If it isn't, you could go to the public library and put it on a USB device and run it that way.

It is on the CD, as far I know.

---

