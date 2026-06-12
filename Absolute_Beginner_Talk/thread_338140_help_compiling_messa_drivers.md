---
title: "help compiling messa drivers"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by L_o_N_e_R on 2007-01-14
[http://mesa3d.sourceforge.net/](http://mesa3d.sourceforge.net/)

i need the latest one 6.5.2

can someone help me compile it?

or even better do it for me :)

thnx for the help

---

### Post by L_o_N_e_R on 2007-01-14
bump^

---

### Post by po0f on 2007-01-14
L_o_N_e_R,

[Link](http://psychocats.net/ubuntu/installingsoftware).

Extract the downloaded archive somewhere you have write permission (your home directory, for example).  Create a new directory where you can keep the source available, name it something like src (`mkdir ~/src`).  (If you're like me, you compile quite a bit from source; I actually suggest using /usr/local/src for this, but that requires 'sudo' access.)
```
[FONT="Courier New"]$ mkdir ~/src
$ cd ~/src
$ tar xvjf /path/to/MesaLib-6.5.2.tar.bz2 # if you downloaded this file...
$ tar xvzf /path/to/MesaLib-6.5.2.tar.gz  # or if you downloaded this one
$ cd MesaLib-6.5.2[/FONT]
```

From here, it depends on the directory contents.  The most common steps taken to compile software is `./configure && make && sudo make install` or `./configure && make && sudo checkinstall`.  You might have to satisfy MesaLib's dependencies before trying to compile it though.

Post back any errors.

---

### Post by L_o_N_e_R on 2007-01-27
sorry for the late reply...been busy

im getting this error


loner@loner-laptop:~/src$ tar xvzf ~/desktop/MesaLib-6.5.2.tar.gz
tar: /home/loner/desktop/MesaLib-6.5.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


and its there too :(

what am i doing wrong?

edit:
ok i tarred it 

when trying to install i get this 

loner@loner-laptop:~/src/Mesa-6.5.2$ ./configure
bash: ./configure: No such file or directory
loner@loner-laptop:~/src/Mesa-6.5.2$ make
make: *** No targets specified and no makefile found.  Stop.
loner@loner-laptop:~/src/Mesa-6.5.2$ sudo make install

edit2:
now i get this


Please choose a configuration from the following list:
aix
aix-64
aix-64-static
aix-gcc
aix-static
beos
darwin
darwin-static
darwin-static-x86ppc
darwin-x86ppc
diffs
diffs~
freebsd
freebsd-dri
freebsd-dri-amd64
freebsd-dri-x86
hpux10
hpux10-gcc
hpux10-static
hpux11-32
hpux11-32-static
hpux11-32-static-nothreads
hpux11-64
hpux11-64-static
hpux11-ia64
hpux11-ia64-static
hpux9
hpux9-gcc
irix6-64
irix6-64-static
irix6-n32
irix6-n32-static
irix6-o32
irix6-o32-static
linux
linux-alpha
linux-alpha-static
linux-debug
linux-directfb
linux-dri
linux-dri-bp
linux-dri-ppc
linux-dri-x86
linux-dri-x86-64
linux-dri-xcb
linux-fbdev
linux-glide
linux-ia64-icc
linux-ia64-icc-static
linux-icc
linux-icc-static
linux-indirect
linux-osmesa
linux-osmesa16
linux-osmesa16-static
linux-osmesa32
linux-ppc
linux-ppc-static
linux-profile
linux-solo
linux-solo-ia64
linux-solo-x86
linux-sparc
linux-sparc5
linux-static
linux-tcc
linux-ultrasparc
linux-x86
linux-x86-32
linux-x86-64
linux-x86-64-debug
linux-x86-64-static
linux-x86-debug
linux-x86-glide
linux-x86-static
netbsd
openbsd
osf1
osf1-static
solaris-x86
solaris-x86-gcc
solaris-x86-gcc-static
sunos4
sunos4-gcc
sunos4-static
sunos5
sunos5-64-gcc
sunos5-gcc
sunos5-smp
sunos5-v8
sunos5-v8-static
sunos5-v9
sunos5-v9-static
ultrix-gcc

Then type 'make <config>' (ex: 'make linux-x86')
(ignore the following error message)
make: *** [configs/current] Error 1


um which one do i use?

---

### Post by L_o_N_e_R on 2007-01-27
ok i used installed checkinstall and used it...

for the make i used "make linux-x86"

i ran the deb file but nothing happned...

---

### Post by L_o_N_e_R on 2007-01-27
this thime i used sudo make install

gave me this

loner@loner-laptop:~/src/Mesa-6.5.2$ sudo make install
make[1]: Entering directory `/home/loner/src/Mesa-6.5.2/src'
make[2]: Entering directory `/home/loner/src/Mesa-6.5.2/src/mesa'
make[3]: Entering directory `/home/loner/src/Mesa-6.5.2/src/mesa'
make[4]: Entering directory `/home/loner/src/Mesa-6.5.2/src/mesa/x86'
make[4]: Nothing to be done for `default'.
make[4]: Leaving directory `/home/loner/src/Mesa-6.5.2/src/mesa/x86'
make[4]: Entering directory `/home/loner/src/Mesa-6.5.2/src/mesa/x86-64'
make[4]: Nothing to be done for `default'.
make[4]: Leaving directory `/home/loner/src/Mesa-6.5.2/src/mesa/x86-64'
make[3]: Leaving directory `/home/loner/src/Mesa-6.5.2/src/mesa'
../../bin/minstall -d /usr/local/include/GL
../../bin/minstall -d /usr/local/lib
../../bin/minstall -m 644 ../../include/GL/*.h /usr/local/include/GL
make[2]: Leaving directory `/home/loner/src/Mesa-6.5.2/src/mesa'
make[2]: Entering directory `/home/loner/src/Mesa-6.5.2/src/glu'
../../bin/minstall -d /usr/local/lib
../../bin/minstall ../../lib/libGLU.* /usr/local/lib
make[2]: Leaving directory `/home/loner/src/Mesa-6.5.2/src/glu'
make[2]: Entering directory `/home/loner/src/Mesa-6.5.2/src/glut/glx'
../../../bin/minstall -d /usr/local/include/GL
../../../bin/minstall -d /usr/local/lib
../../../bin/minstall -m 644 ../../../include/GL/glut.h /usr/local/include/GL
../../../bin/minstall ../../../lib/libglut* /usr/local/lib
make[2]: Leaving directory `/home/loner/src/Mesa-6.5.2/src/glut/glx'
make[2]: Entering directory `/home/loner/src/Mesa-6.5.2/src/glw'
../../bin/minstall -d /usr/local/include/GL
../../bin/minstall -d /usr/local/lib
../../bin/minstall -m 644 *.h /usr/local/include/GL
../../bin/minstall ../../lib/libGLw.* /usr/local/lib
make[2]: Leaving directory `/home/loner/src/Mesa-6.5.2/src/glw'
make[1]: Leaving directory `/home/loner/src/Mesa-6.5.2/src'
make[1]: Entering directory `/home/loner/src/Mesa-6.5.2/progs'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/loner/src/Mesa-6.5.2/progs'


what do you think is the prob?

---

### Post by deepclutch on 2007-05-03
WRong compilation.U must read mesa docs dir for howto.U also need devel files installed.also there seems problem compiling as xcb is introduced :popcorn:

---

