---
title: "Help! I can't get gcc or cpp to install!"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-09-30
Hello..
I am new to Ubuntu and relatively new to Linux.  I am trying to compile libdvdcss but when I run ./configure, I get:

-prefix=/usr
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

When I run rpmverify gcc and rpmverify cpp, I get "not installed" for both.  
I downloaded the rpm for gcc but I don't know how to install or configure it... So, my question is, How do I get gcc and cpp working with the least amount of hassle? Thanks in advance!!

---

### Post by K.Mandla on 2006-09-30
Without sounding snotty, if you're after the libdvdcss stuff, why not try 

[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

It's a far cry easier than compiling things. But I think if you want gcc and cpp you could

```
sudo aptitude install gcc cpp
```
or even add *build-essential* to that. 

Hope that helps. :)

---

### Post by saintj0n on 2006-09-30
You are right, I tried both ways and that was easier.  However, when trying to do the sudo aptitude gcc cpp, I get an error:

install cpp gcc
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  libssl0.9.8 openssl
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
jonathan@jonathan-laptop:/usr/local/lib/libdvdcss/libdvdcss-1.2.9$ rpmverify gcc
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm
package gcc is not installed

Ultimately, I'm sure I will need gcc or cpp to install packages on my system and it would be helpful to know how. Are rpm files less useful on Ubuntu?  I have never heard of alien.
Thanks from a newbie!

---

### Post by hyper_ch on 2006-09-30
isn't it:

```

apt get-install gcc-3.4

```

?

---

### Post by podunk on 2006-09-30
If you look at the top of your desktop you will see
System 
and in that menu you will find
Administration>Synaptic Package manager

Click this, enter your password. Click “Search” then enter
build-essential

Go down the list til you get to build-essential right click and “Mark for Install.”  You might want to install the docs also.

Click search and look for 
checkinstall

mark it, then click the green check mark “Apply” then confirm your choice.

This should contain all the c and g compilers you need. If not go back to the package manager and search for them and install them.

/.configure
make

after you “make” you can use the 
```
checkinstall
```
command to install your program. This makes it easy to uninstall it later on.

If you're new I would suggest against messing with rpm stuff at the start. Most of everything you will need is in the package manager.

---

### Post by lacis_alfredo on 2007-05-19
I also got this configure error, tyring to install libieee1284 (parallel port driver required by my scanner):

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

I *THEN* tried installing "build-essentials", and get the Dialog "Mark additional required changes?" with:
      To be installed
               dpkg-dev

I clicked on "Mark" but got this Error Dialog "Could not mark all packages for installation or upgrade" with this in the text field:
build-essential:
 Depends: g++ but it is not going to be installed

This is all bl**dy strange, because I have Green Boxes against:
gcc, gcc-3.3, gcc-3.3-base, gcc-3.4, gcc-3.4-base, gcc-4.0, gcc-4.0-base, gcc-4.1  

I *THEN* tried installing "g++", and I get this Error Dialog:
g++:
  Depends: cpp (>=4:4.1.2-1ubuntu1) but 4:4.1.1-6ubuntu3 is to be installed
  Depends: gcc (>=4:4.1.2-1ubuntu1) but 4:4.1.1-6ubuntu3 is to be installed
 Depends: g++-4.1 but it is not going to be installed
  Depends: gcc-4.1 (>=4.1.2) but 4.1.1-13ubuntu5 is to be installed

What is going on?

This is just a compiler: it's like a handful of programs: you use these to compile source code.

Why is everything so *obfuscated*?  

I wanna compile one little program!!!!!!!

It used to be: download compiler, bootstrap it via bison, etc.  

Then compile your programs ....  then happy user :)

Now it's package this, package that, 
EVERYTHING IS /H/I/D/D/E/N/, ----
I_ _D_O_N_'_T_ _W_A_N_T_ _A_N_ _E_X_P_E_R_I_E_N_C_E_ -- 

I WANT A *C*O*M*P*U*T*E*R*.

If I want an experience, I go for a swim or take my dog for a walk.

---

### Post by %hMa@?b&lt;C on 2007-05-19
sudo aptitude install build-essential autoconf automake bison flex checkinstall
./configure
make 
sudo checkinstall

---

### Post by Bachstelze on 2007-05-19
Do't bother to install gcc, g++ and all that. Install *build-essential*, it has all you need :)

Actually, those errors you gett seem to indicate there's a problem with your softare sources. Could you please paste your /etc/apt/sources.list ?

---

### Post by taurus on 2007-05-19
First thing you should do is to calm down...

What happens when you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
```
And if you get any error message, post the whole error message here and also your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

