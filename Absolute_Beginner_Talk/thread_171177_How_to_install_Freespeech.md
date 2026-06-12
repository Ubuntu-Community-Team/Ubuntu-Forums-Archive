---
title: "How to install Freespeech ??"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-05-06
Hi ,
 
I did this : 
 
1/ FIRST  
with libtool 1.3.3. 
(I did ./configure; make ; make install)
   
2/ SECOND
```
#!/bin/bash
apt-get -f install gnome-libs-data libgnomeui-0 gconf libgdk-pixbuf2 libgdk-pixbuf-dev gnome-vfs-extfs libgnomevfs2-common libgnomeprint15 libgnomeprint-data libgnomeprint-dev libgnome-vfs0 libgnome-vfs-common libgnome-vfs-dev libgal-dev libgal2.0-6 libgal2.0-common libgal-data
apt-get -f install hamlib3 hamlib-dev

apt-get -f -y install gnome-common

# remove all automake plz

apt-get -f -y install automake1.4
apt-get -f -y install aclocal
apt-get -f -y install autoconf
apt-get -f -y install cvs
apt-get -f -y install libtool 
apt-get -f -y install make
apt-get -f -y install doc++
apt-get -f -y install perl
apt-get -f -y install m4
apt-get -f -y install libxml-dev

apt-get -f -y install fftw3
apt-get -f -y install fftw-dev
(no need of vflow maybe)


aclocal
automake
autoconf
echo "type ./configure"
echo "**"
./configure --enable-float --enable-shared
make 
make install


```
  
Help !

---

### Post by patrick295767 on 2006-05-06
My error msg : 

```
creating libtool
loading cache /dev/null
checking for c++... c++
checking whether the C++ compiler (c++   ) works... yes
checking whether the C++ compiler (c++   ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking whether make sets ${MAKE}... (cached) yes
checking for sin in -lm... yes
updating cache /dev/null
creating ./config.status
creating Makefile
creating include/Makefile
creating src/Makefile
Making all in data-flow
make[1]: Entering directory `/root/FreeSpeech-0.1.2/data-flow'
Making all in src
make[2]: Entering directory `/root/FreeSpeech-0.1.2/data-flow/src'
/bin/sh ../../libtool --mode=compile g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DLINUX=1 -DPROTOTYPES=1 -DHAVE_LIBM=1 -DHAVE_LIBDL=1 -DHAVE_LIBPTHREAD=1  -I. -I.  -I../../data-flow/include    -g -O2 -c Node.cc
libtool: ltconfig version `' does not match ltmain.sh version `1.3.3'
Fatal configuration error.  See the libtool docs for more information.
make[2]: *** [Node.lo] Error 1
make[2]: Leaving directory `/root/FreeSpeech-0.1.2/data-flow/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/FreeSpeech-0.1.2/data-flow'
make: *** [all-recursive] Error 1
Making install in data-flow
make[1]: Entering directory `/root/FreeSpeech-0.1.2/data-flow'
Making install in src
make[2]: Entering directory `/root/FreeSpeech-0.1.2/data-flow/src'
/bin/sh ../../libtool --mode=compile g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DLINUX=1 -DPROTOTYPES=1 -DHAVE_LIBM=1 -DHAVE_LIBDL=1 -DHAVE_LIBPTHREAD=1  -I. -I.  -I../../data-flow/include    -g -O2 -c Node.cc
libtool: ltconfig version `' does not match ltmain.sh version `1.3.3'
Fatal configuration error.  See the libtool docs for more information.
make[2]: *** [Node.lo] Error 1
make[2]: Leaving directory `/root/FreeSpeech-0.1.2/data-flow/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/root/FreeSpeech-0.1.2/data-flow'
make: *** [install-recursive] Error 1

```
  
I dont understand 'cos I remove libtool
and got the 1.3.3 from the tar.gz
hwo to check that s all right ??

thank you __

---

