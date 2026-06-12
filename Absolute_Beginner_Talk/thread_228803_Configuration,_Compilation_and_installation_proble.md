---
title: "Configuration, Compilation and installation problem"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by ubuntian on 2006-08-03
do anyone willing to tell me y there is no respone on terminal after i unpacking the fuse 2.5.3 package(i had change the terminal directory where the unpacked file located) and type:

./configure
make
make install

the terminal show msg like this:-
nio@niomachine:~/fuse-2.5.3$ ./configure
bash: ./configure: No such file or directory
nio@niomachine:~/fuse-2.5.3$ make
bash: make: command not found
nio@niomachine:~/fuse-2.5.3$ make install
bash: make: command not found
nio@niomachine:~/fuse-2.5.3$

is that my way of typing improper???:confused: :confused:

---

### Post by zxee on 2006-08-03
I'm not familar with fuse but I have spent lots of time compiling programs-well attempting to.. :)
The best 1st step is always the included README. 
Sometimes a program isn't installed through the ./configure, make, sudo make install dance. 
So that's what I have to offer-what does the README tell you about installing that package?

---

### Post by gizmoarena on 2006-08-03
i guess your archive didnt have the configure file. you have to make a configure file from configure.ac [i donno yet how to do this]

the major fact is if you are using ubuntu / kubuntu, you'll need a C/C++ compiler to compile the installer. 

you can get it from here 

> sudo apt-get build-dep tcl8.4-dev tk8.4-dev

---

### Post by ubuntian on 2006-08-04
now the problem is that i can ./configure it but the make and make install doesn't work....

nio@niomachine:~$ cd fuse-2.5.3/
nio@niomachine:~/fuse-2.5.3$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for style of include used by make... none
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... none
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from  object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) none
checking for fork... yes
checking for setxattr... yes
checking for fdatasync... yes
checking for struct stat.st_atim... yes
configure: creating ./config.status
config.status: creating fuse.pc
config.status: creating Makefile
config.status: creating lib/Makefile
config.status: creating util/Makefile
config.status: creating example/Makefile
config.status: creating include/Makefile
config.status: creating include/config.h
config.status: executing depfiles commands
config.status: executing libtool commands
configure: configuring in kernel
configure: running /bin/sh './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking if FUSE is loaded as a module... yes
checking if FUSE module is from official kernel... yes
configure: NOTE:     Detected that FUSE is already present in the kernel, so
configure: NOTE:     building of kernel module is disabled.  To force building
configure: NOTE:     of kernel module use the '--enable-kernel-module' option.
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
[B][COLOR="Red"]nio@niomachine:~/fuse-2.5.3$ make
bash: make: command not found[/COLOR][/B]
nio@niomachine:~/fuse-2.5.3$

---

### Post by Tomosaur on 2006-08-04
sudo apt-get install make

It's not installed by default :/

---

### Post by ubuntian on 2006-08-04
> **Tomosaur said:**
> sudo apt-get install make

It's not installed by default :/

thx man! i get it done! thank you very much again!:D :D :D

---

### Post by patrick295767 on 2006-08-04
> **ubuntian said:**
> do anyone willing to tell me y there is no respone on terminal after i unpacking the fuse 2.5.3 package(i had change the terminal directory where the unpacked file located) and type:

./configure
make
make install

the terminal show msg like this:-
nio@niomachine:~/fuse-2.5.3$ ./configure
bash: ./configure: No such file or directory
nio@niomachine:~/fuse-2.5.3$ make
bash: make: command not found
nio@niomachine:~/fuse-2.5.3$ make install
bash: make: command not found
nio@niomachine:~/fuse-2.5.3$

is that my way of typing improper???:confused: :confused:

 
You need to have at least to feel good with ur machine: 
```

apt-get update
################ make install !! ##############"
## this 3  lines for amsn 0.95 & also for vmware workstation
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install tcl8.4 
apt-get -f -y install tk8.4
apt-get -f -y install tk8.4-dev

## for building, make ... checkinstall
apt-get install -f -y kdevelop kdevelop3-dev build-essential checkinstall

##### amsn  installation
apt-get -f -y install gcc 
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
apt-get -f -y install linux-headers-$(uname -r)
apt-get -f -y install build-essential 


## voor vmware
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential 
apt-get -f -y install zenity
apt-get -f -y install linux-tree
apt-get -f -y install g++-3.4
cat /proc/version
ls /usr/bin/gcc*
rm -rf /usr/src/linux
apt-get -f -y install linux-headers-$(uname -r)
ls /usr/bin/gcc*
ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
rm /usr/bin/gccbug
ln -s /usr/bin/gccbug-3.4 /usr/bin/gccbug
CC=/usr/bin/gcc-3.4
export CC
apt-get -f -y install
apt-get -f -y install

######## installing qt3
apt-get -f -y install qt3-dev-tools
apt-get -f -y install qt3-apps-dev
apt-get -f -y install libqt3-headers
apt-get -f -y install qca-dev
apt-get -f -y install libqt3c102-mt
export QTDIR=/usr/share/qt3

##########end ###### make install !! ##############"

```

---

