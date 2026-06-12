---
title: "'invalid lvalue in assingment' - installing regviewer"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by xeb07170 on 2007-12-17
Hi,

I am new to linux and I am currently doing a one year forensics course. We have taken an image of a suspect computer and will investigate this image. This would be no problem in the labs in the university - it is just I am at home. 

My knowledge is poor, infact - we dont even start the computing aspect of it until next semester.

I have installed kubuntu and through much frustration, i have managed to install gtk and everything needed to install that.

I am now trying to install regviewer. I can run the ./configure command without any problems, it is only when i attempt the 'make' command i get issues.

The following is the output i receive



root@paul-desktop:~# cd /home/paul/Desktop/regviewer-0.1/
root@paul-desktop:~/Desktop/regviewer-0.1# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
root@paul-desktop:~/Desktop/regviewer-0.1# make
make  all-recursive
make[1]: Entering directory `/home/paul/Desktop/regviewer-0.1'
Making all in src
make[2]: Entering directory `/home/paul/Desktop/regviewer-0.1/src'
gcc -DHAVE_CONFIG_H -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -pthread -DORBIT2=1 -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/pango-1.0 -I/usr/include/freetype2 -I/usr/local/include/atk-1.0 -I/usr/local/include/cairo -I/usr/local/include/libpng12 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0 -I/usr/lib/gtk-2.0/include      -g -O2 -MT ntreg.o -MD -MP -MF .deps/ntreg.Tpo -c -o ntreg.o ntreg.c
ntreg.c: In function &#8216;put_dword&#8217;:
ntreg.c:1999: error: invalid lvalue in assignment
make[2]: *** [ntreg.o] Error 1
make[2]: Leaving directory `/home/paul/Desktop/regviewer-0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/paul/Desktop/regviewer-0.1'
make: *** [all] Error 2
root@paul-desktop:~/Desktop/regviewer-0.1# make check
Making check in src
make[1]: Entering directory `/home/paul/Desktop/regviewer-0.1/src'
gcc -DHAVE_CONFIG_H -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -pthread -DORBIT2=1 -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/pango-1.0 -I/usr/include/freetype2 -I/usr/local/include/atk-1.0 -I/usr/local/include/cairo -I/usr/local/include/libpng12 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0 -I/usr/lib/gtk-2.0/include      -g -O2 -MT ntreg.o -MD -MP -MF .deps/ntreg.Tpo -c -o ntreg.o ntreg.c
ntreg.c: In function &#8216;put_dword&#8217;:
ntreg.c:1999: error: invalid lvalue in assignment
make[1]: *** [ntreg.o] Error 1
make[1]: Leaving directory `/home/paul/Desktop/regviewer-0.1/src'
make: *** [check-recursive] Error 1
root@paul-desktop:~/Desktop/regviewer-0.1# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
root@paul-desktop:~/Desktop/regviewer-0.1# make check
Making check in src
make[1]: Entering directory `/home/paul/Desktop/regviewer-0.1/src'
gcc -DHAVE_CONFIG_H -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -pthread -DORBIT2=1 -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/pango-1.0 -I/usr/include/freetype2 -I/usr/local/include/atk-1.0 -I/usr/local/include/cairo -I/usr/local/include/libpng12 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0 -I/usr/lib/gtk-2.0/include      -g -O2 -MT ntreg.o -MD -MP -MF .deps/ntreg.Tpo -c -o ntreg.o ntreg.c
ntreg.c: In function &#8216;put_dword&#8217;:
ntreg.c:1999: error: invalid lvalue in assignment
make[1]: *** [ntreg.o] Error 1
make[1]: Leaving directory `/home/paul/Desktop/regviewer-0.1/src'
make: *** [check-recursive] Error 1
root@paul-desktop:~/Desktop/regviewer-0.1# man cls
No manual entry for cls
root@paul-desktop:~/Desktop/regviewer-0.1# cl
The program 'cl' is currently not installed.  You can install it by typing:
apt-get install cl-launch
bash: cl: command not found
root@paul-desktop:~/Desktop/regviewer-0.1# clear






root@paul-desktop:~/Desktop/regviewer-0.1# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
root@paul-desktop:~/Desktop/regviewer-0.1# make
make  all-recursive
make[1]: Entering directory `/home/paul/Desktop/regviewer-0.1'
Making all in src
make[2]: Entering directory `/home/paul/Desktop/regviewer-0.1/src'
gcc -DHAVE_CONFIG_H -I. -I.. -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\" -pthread -DORBIT2=1 -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/local/include/pango-1.0 -I/usr/include/freetype2 -I/usr/local/include/atk-1.0 -I/usr/local/include/cairo -I/usr/local/include/libpng12 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0 -I/usr/lib/gtk-2.0/include      -g -O2 -MT ntreg.o -MD -MP -MF .deps/ntreg.Tpo -c -o ntreg.o ntreg.c
ntreg.c: In function &#8216;put_dword&#8217;:
ntreg.c:1999: error: invalid lvalue in assignment
make[2]: *** [ntreg.o] Error 1
make[2]: Leaving directory `/home/paul/Desktop/regviewer-0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/paul/Desktop/regviewer-0.1'
make: *** [all] Error 2
root@paul-desktop:~/Desktop/regviewer-0.1#     




any ideas? been trying to install since last night.

Thanks

---

### Post by spiderbatdad on 2007-12-17
have you installed the package "build-essential" from synaptic?

---

### Post by xeb07170 on 2007-12-17
no - i have not - will do and post back

---

### Post by xeb07170 on 2007-12-17
actually - it is installed, just checked the package manager

---

### Post by spiderbatdad on 2007-12-17
Also...assuming you did:```
sudo apt-get install cl-launch
```

---

### Post by xeb07170 on 2007-12-17
yep

---

### Post by spiderbatdad on 2007-12-17
so build essential is marked green as in installed, because it isnt installed by default. It is only listed as a package capable of being installed. Sorry if this sounds lame to you, but not everyone realizes this, and I don't know your level of familiarity. Again sorry.

---

### Post by xeb07170 on 2007-12-17
dont worry, does not sound lame - have only really been using for last 48 hours - tried ubuntu and kubunti - kubuntu is the one we use in uni so i stick to that - ubuntu has synaptic, kubuntu has adept.

The package is marked as green and is installed.

tried doing some searches for this online - cant seem to make sense of it.

---

### Post by spiderbatdad on 2007-12-17
I'm thinking there is a problem with the C compiler. maybe gcc is not the right version. there are several versions listed in synaptic. You might try a different C compiler. Hope this helps. I read your output and see that it is accepting whatever version of gcc you have, but later the lvalue assignment problem occurs. This suggests a problem with C compiler

---

### Post by xeb07170 on 2007-12-17
i already have, i tried upgrading to 4.2 from 4.1 - didnt help

i might try an earlier version and see if it that works

thanks

---

### Post by xeb07170 on 2007-12-17
now i have other probs, it states that no acceptable compiler was found

---

### Post by spiderbatdad on 2007-12-17
personally i would add g++ and gawk, and go back to the version of gcc you had

---

### Post by xeb07170 on 2007-12-18
nothing has worked, was shattered had to go to bed - finally got the c compiler working again but I am left with the original problem - anyone any ideas???

---

### Post by spiderbatdad on 2007-12-18
This is a glade-2 based project.  You must have GTK+ 2.2 installed in order
to run RegViewer. You can find it here: [http://www.gtk.org/](http://www.gtk.org/)

The following steps should build regviewer

   1. extract the tarball
      tar -xvzf regviewer-0.1.tar.gz
   2. configure the software
      cd regviewer-0.1
     ** ./autogen.sh**
   3. compile the software
      make
   4. Optionally install the software
      make install


to run ./autogen.sh you're going to need autoconf and automake, so you'll want to make sure those are installed.  Must be I'm looking at a different package...now that i look back, i see yours has a configuration file and this one doesn't...that's why autogen is used...maybe get the tar.gz from sourceforge and start over with a new package...it's not like this one is working and you're switching.

---

