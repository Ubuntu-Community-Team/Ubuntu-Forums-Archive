---
title: "install stuff..."
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Fittersman on 2006-11-02
ok honestly this is probably easy but i cant figure it out....

i want to install these package i have downloaded

qpspmanager-1.3.tar.gz

HandBrake-0.7.1.tar.gz

pspvc-install-0.2.1.tar.gz




i just cant do it....](*,)

---

### Post by PPAAUULL on 2006-11-02
Did you check the repos for the programs first?

---

### Post by whiterabbit on 2006-11-02
First, to save yourself some time, do...

```
apt-cache search ...........
```
If it's there...
```
sudo apt-get install ........
```
or...
```
sudo aptitude install ........
```

If that isn't any help, have a read of [this install guide](http://www.tuxfiles.org/linuxhelp/softinstall.html).

---

### Post by po0f on 2006-11-02
Fittersman,

Try unpacking them and actually reading the README file?  You didn't post anything about errors, so I can only assume you didn't even try beyond downloading the files.

---

### Post by user1397 on 2006-11-02
to learn how to install any kind of file in ubuntu, try this: [http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)

---

### Post by Fittersman on 2006-11-04
here is the readme

```
QPPSPManager
The Linux PSP File Manager
(C) 2006 Bernat Ràfales Mulet (see COPYING for license details)

Installation instructions
=========================

First, be sure you have the QT3 Development files, then just type

qmake

to build the Makefile, then

make

to build the project, and finally

make install

to install the program (you should execute make install with root permission).

Then you will have the binary "qpspmanager" for your enjoyment.

I strongly recommend changing the default "style" for QT, which is KeramiK, to
another one more better looking such as PlastiK.

```

i typed qmake in and it says that there is no such command as qmake and guy that told me to go to the terminal and do stuff (whiterabbit) i did and i think its already downloaded because it says there is no files to download

---

### Post by PriceChild on 2006-11-04
You will need to ```
sudo apt-get install build-essential
```in order to build programs.

---

### Post by taurus on 2006-11-04
You first need a compile so install it with

```
sudo aptitude update
sudo aptitude install build-essential
```
Then, build and install it with

```
./configure
make
sudo make install
-or-
sudo make checkinstall <-- this option is better than the one above...
```

---

### Post by PriceChild on 2006-11-04
> **taurus said:**
> ```

sudo make checkinstall <-- this option is better than the one above...
```Basically because this option creates a "deb" package, which you can easily manage using synaptic or apt.

make install just installs the files requiring you to keep the folder and use "make uninstall" to get rid of the app.

---

### Post by Fittersman on 2006-11-04
cleippi@FamilyComputer:~/Desktop/HandBrake-0.7.1$ ./configure
System: Linux
Endian: little

To build HandBrake, run 'jam'.
cleippi@FamilyComputer:~/Desktop/HandBrake-0.7.1$ jam
bash: jam: command not found

---

### Post by taurus on 2006-11-04
```
./jam
```

---

### Post by blendmaster on 2006-11-04
> To build HandBrake, run 'jam'.
cleippi@FamilyComputer:~/Desktop/HandBrake-0.7.1$ jam
bash: jam: command not found

jam is most likely a file. In that directory run:

```
./jam
```

and it should run that file.

I've never had much luck compiling from source, so I wish you good luck!

---

### Post by po0f on 2006-11-04
It's probably referring to [Boost Jam](http://www.boost.org/tools/build/jam_src/index.html) which is [in the repos](http://packages.ubuntu.com/edgy/devel/bjam).

---

### Post by Fittersman on 2006-11-04
cleippi@FamilyComputer:~/Desktop/HandBrake-0.7.1$ ./jam
bash: ./jam: No such file or directory

and that last comment i have no idea what those websites are trying to say it is total gibberish....

---

### Post by po0f on 2006-11-04
Fittersman,

It's in the repos, meaning you can apt-get it.
```
$ sudo aptitude install bjam
```

---

### Post by Fittersman on 2006-11-04
cleippi@FamilyComputer:~/Desktop/HandBrake-0.7.1$ jam
libhb/Jamfile:18: in SubInclude
rule ObjectDefines unknown in module
Jamfile:75: in module scope
cleippi@FamilyComputer:~/Desktop/HandBrake-0.7.1$

---

### Post by po0f on 2006-11-04
Fittersman,

Looks like whoever distributed that program doesn't know how to write a Jamfile, kindly let them know that they suck.  :)

---

### Post by Fittersman on 2006-11-04
lol.... ok so now what about qpspmanager-1.3.tar.gz and pspvc-install-0.2.1.tar.gz i dont even know where to get started with those, like is there an exe type file i could use because i liked that about windows, look for the .exe file and start it up...

---

### Post by po0f on 2006-11-05
Fittersman,

Are these files downloaded to your Desktop?  I hope so, here we go!

Open up a terminal and issue the following commands:
```
$ cd Desktop
$ tar -xvzf qpspmanager-1.3.tar.gz
$ cd qpspmanager-1.3
$ ./configure
$ make
$ sudo make checkinstall
```

If you have problems with checkinstall, make sure it's installed first:
```
$ sudo aptitude update
$ sudo aptitude install checkinstall
```

And just follow the same procedure for the other one.  If you get complaints about missing libraries, post back.

---

### Post by taurus on 2006-11-05
If you need to install something extra on your machine, try using synaptic/apt-get/aptitude whenever you can.  It saves you time and energy.  Unless something is not available for Ubuntu and you can't find it in the repos, then you would install it from source.  Here are a couple of links for you to read over about installing stuff in Ubuntu...

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by po0f on 2006-11-05
Fittersman,

Ok I lied, I'm sorry.  I didn't realize qpspmanager was a Qt app.
```
$ sudo aptitude install libqt libqt-mt qt3-dev-tools libqt3-headers libqt3-mt-dev
$ cd Desktop
$ tar -xvzf qpspmanager-1.3.tar.gz
$ cd qpspmanager-1.3
$ qmake
$ make
$ sudo checkinstall -D
```

[EDIT]

Changed install command.

---

### Post by Fittersman on 2006-11-05
cleippi@FamilyComputer:~/Desktop/qpspmanager-1.3$ ./configure
bash: ./configure: No such file or directory

---

### Post by taurus on 2006-11-05
> **Fittersman said:**
> cleippi@FamilyComputer:~/Desktop/qpspmanager-1.3$ ./configure
bash: ./configure: No such file or directory
What's the output of this command then?

```
ls -la
```

---

### Post by Fittersman on 2006-11-05
cleippi@FamilyComputer:~/Desktop/qpspmanager-1.3$ ls -la
total 44
drwxr-xr-x 3 cleippi cleippi  4096 2006-08-28 06:40 .
drwxr-xr-x 8 cleippi cleippi  4096 2006-11-04 22:58 ..
-rw-r--r-- 1 cleippi cleippi  2172 2006-08-25 09:23 Changelog
-rw-r--r-- 1 cleippi cleippi 18009 2006-07-28 08:12 COPYING
-rw-r--r-- 1 cleippi cleippi   130 2006-07-28 08:12 qpspmanager.pro
-rw-r--r-- 1 cleippi cleippi   590 2006-08-25 09:31 README
drwxr-xr-x 5 cleippi cleippi  4096 2006-08-28 06:32 src

---

### Post by po0f on 2006-11-05
Fittersman,

Hint, read my last post in this thread.

[EDIT]

And that last line of commands probably should be:
```
$ sudo checkinstall -D
```

I've used it once before, I'm used to manually installing stuff.

---

### Post by taurus on 2006-11-05
It's probably in src directory.  What does README say anyway?

```
cd src
./configure
```

---

### Post by Fittersman on 2006-11-05
lol sorry poof but im a complete moron.... can you help me out?

---

### Post by po0f on 2006-11-05
Fittersman,

[Click](http://www.ubuntuforums.org/showpost.php?p=1715953&postcount=21).

---

### Post by Fittersman on 2006-11-05
cleippi@FamilyComputer:~/Desktop/qpspmanager-1.3$ sudo checkinstall -D
sudo: checkinstall: command not found

---

### Post by po0f on 2006-11-05
Fittersman,

```
$ sudo aptitude install checkinstall
$ sudo checkinstall -D
```

---

### Post by Fittersman on 2006-11-05
k i did all that and it was a sucess but now how do i use this program "please be simple" :D

---

### Post by po0f on 2006-11-05
Fittersman,

You should be able to just open up a terminal and type:
```
$ qpspmanager
```

---

### Post by Fittersman on 2006-11-05
o sweet you rock man/woman

---

### Post by Fittersman on 2006-11-05
new problem i tried doin the samething but with a different program and here is what happend...

```
cleippi@FamilyComputer:~/Desktop/pspvc-install-0.2.1$ qmake -makefile
Usage: qmake [mode] [options] [files]

   QMake has two modes, one mode for generating project files based on
some heuristics, and the other for generating makefiles. Normally you
shouldn't need to specify a mode, as makefile generation is the default
mode for qmake, but you may use this to test qmake on an existing project

Mode:
        -project       Put qmake into project file generation mode
                       In this mode qmake interprets files as files to
                       be built,
                       defaults to *.c; *.ui; *.y; *.l; *.ts; *.h; *.hpp; *.hh; *.H; *.hxx; *.cpp; *.cc; *.cxx; *.C
        -makefile      Put qmake into makefile generation mode (default)
                       In this mode qmake interprets files as project files to
                       be processed, if skipped qmake will try to find a project                       file in your current working directory

Warnings Options:
        -Wnone         Turn off all warnings
        -Wall          Turn on all warnings
        -Wparser       Turn on parser warnings
        -Wlogic        Turn on logic warnings

Options:
         * You can place any variable assignment in options and it will be     *         * processed as if it was in [files]. These assignments will be parsed *         * before [files].                                                     *        -o file        Write output to file
        -unix          Run in unix mode
        -win32         Run in win32 mode
        -macx          Run in Mac OS X mode
        -d             Increase debug level
        -t templ       Overrides TEMPLATE as templ
        -tp prefix     Overrides TEMPLATE so that prefix is prefixed into the value
        -help          This help
        -v             Version information
        -after         All variable assignments after this will be
                       parsed after [files]
        -cache file    Use file as cache           [makefile mode only]
        -spec spec     Use spec as QMAKESPEC       [makefile mode only]
        -nocache       Don't use a cache file      [makefile mode only]
        -nodepend      Don't generate dependencies [makefile mode only]
        -nomoc         Don't generate moc targets  [makefile mode only]
        -nopwd         Don't look for files in pwd [ project mode only]
        -norecursive   Don't do a recursive search [ project mode only]

```

---

### Post by po0f on 2006-11-05
Fittersman,

The reason you needed to do that with qpspmanager was because it was a Qt app.  Not everything in Linux is built the same way, so you will probably have to perform the usual configure/make/sudo checkinstall dance:
```
$ cd ~/Desktop/pspvc-install-0.2.1
$ ./configure
$ make
$ sudo checkinstall -D
```

---

### Post by Fittersman on 2006-11-05
cleippi@FamilyComputer:~/Desktop/pspvc-install-0.2.1$ ./configure
bash: ./configure: No such file or directory

---

### Post by po0f on 2006-11-05
Fittersman,

Can you post the results of:
```
$ ls -l ~/Desktop/pspvc-install-0.2.1
```

---

### Post by Fittersman on 2006-11-05
cleippi@FamilyComputer:~/Desktop/pspvc-install-0.2.1$ ls -l ~/Desktop/pspvc-install-0.2.1
total 20
drwxr-xr-x 2 cleippi cleippi 4096 2006-07-13 05:16 archives
-rwxr-xr-x 1 root    root    1995 2006-11-02 20:20 install
-rwx------ 1 cleippi cleippi 1995 2006-07-13 05:18 install.sh
-rwx------ 1 cleippi cleippi 2001 2006-07-13 05:19 uninstall.sh
drwxr-xr-x 3 cleippi cleippi 4096 2006-11-02 19:20 work

---

### Post by taurus on 2006-11-05
```
sudo ./install.sh
```

---

### Post by po0f on 2006-11-05
Fittersman,

Ok, I just downloaded it and read through the install.sh script.  It looks safe to install, just don't run it with any arguments:
```
$ cd ~/Desktop/pspvc-install-0.2.1
$ sudo ./install.sh
```

From the [website](http://pspvc.sourceforge.net/index.html), you might need to install packages to satisfy these requirements:
[list]
[*] nasm
[*] libfaac
[*] libxvidcore
[*] gtk+2.0
[/list]

Running GNOME, you should have Gtk  ;), but the other ones aren't installed by default.  I don't know if libfaac and libxvidcore are enabled in either universe or multiverse, but I know nasm is in there:
```
$ sudo aptitude install nasm
```

Hope this helps.

[EDIT]

Too slow.

---

### Post by Fittersman on 2006-11-05
alot of stuff happened before this and i think this is the highlights of it

```
nasm -f elf -o common/i386/dct-a.o common/i386/dct-a.asm
make: nasm: Command not found
make: *** [common/i386/dct-a.o] Error 127
ERROR during compilation or installation of X264

```

---

### Post by Fittersman on 2006-11-05
```
cleippi@FamilyComputer:~/Desktop/pspvc-install-0.2.1$ sudo ./install.sh
Password:
mkdir: cannot create directory `work': File exists
x264_051028/
x264_051028/AUTHORS
x264_051028/build/
x264_051028/build/cygwin/
x264_051028/build/cygwin/Makefile
x264_051028/build/win32/
x264_051028/build/win32/libx264.dsp
x264_051028/build/win32/x264.dsp
x264_051028/build/win32/x264.dsw
x264_051028/common/
x264_051028/common/amd64/
x264_051028/common/amd64/cpu-a.asm
x264_051028/common/amd64/dct-a.asm
x264_051028/common/amd64/mc-a.asm
x264_051028/common/amd64/mc-a2.asm
x264_051028/common/amd64/pixel-a.asm
x264_051028/common/amd64/pixel-sse2.asm
x264_051028/common/amd64/predict-a.asm
x264_051028/common/amd64/quant-a.asm
x264_051028/common/bs.h
x264_051028/common/cabac.c
x264_051028/common/cabac.h
x264_051028/common/clip1.h
x264_051028/common/common.c
x264_051028/common/common.h
x264_051028/common/cpu.c
x264_051028/common/cpu.h
x264_051028/common/csp.c
x264_051028/common/csp.h
x264_051028/common/dct.c
x264_051028/common/dct.h
x264_051028/common/display-x11.c
x264_051028/common/display.h
x264_051028/common/frame.c
x264_051028/common/frame.h
x264_051028/common/i386/
x264_051028/common/i386/cpu-a.asm
x264_051028/common/i386/dct-a.asm
x264_051028/common/i386/dct-c.c
x264_051028/common/i386/dct.h
x264_051028/common/i386/mc-a.asm
x264_051028/common/i386/mc-a2.asm
x264_051028/common/i386/mc-c.c
x264_051028/common/i386/mc.h
x264_051028/common/i386/pixel-a.asm
x264_051028/common/i386/pixel-sse2.asm
x264_051028/common/i386/pixel.h
x264_051028/common/i386/predict-a.asm
x264_051028/common/i386/predict.c
x264_051028/common/i386/predict.h
x264_051028/common/i386/quant-a.asm
x264_051028/common/i386/quant.h
x264_051028/common/macroblock.c
x264_051028/common/macroblock.h
x264_051028/common/mc.c
x264_051028/common/mc.h
x264_051028/common/mdate.c
x264_051028/common/pixel.c
x264_051028/common/pixel.h
x264_051028/common/ppc/
x264_051028/common/ppc/dct.c
x264_051028/common/ppc/dct.h
x264_051028/common/ppc/mc.c
x264_051028/common/ppc/mc.h
x264_051028/common/ppc/pixel.c
x264_051028/common/ppc/pixel.h
x264_051028/common/ppc/ppccommon.h
x264_051028/common/predict.c
x264_051028/common/predict.h
x264_051028/common/quant.c
x264_051028/common/quant.h
x264_051028/common/set.c
x264_051028/common/set.h
x264_051028/common/sparc/
x264_051028/common/sparc/pixel.asm
x264_051028/common/sparc/pixel.h
x264_051028/common/visualize.c
x264_051028/common/visualize.h
x264_051028/common/vlc.h
x264_051028/config.mak
x264_051028/configure
x264_051028/COPYING
x264_051028/decoder/
x264_051028/decoder/decoder.c
x264_051028/decoder/macroblock.c
x264_051028/decoder/macroblock.h
x264_051028/decoder/set.c
x264_051028/decoder/set.h
x264_051028/decoder/vlc.c
x264_051028/decoder/vlc.h
x264_051028/doc/
x264_051028/doc/dct.txt
x264_051028/encoder/
x264_051028/encoder/analyse.c
x264_051028/encoder/analyse.h
x264_051028/encoder/cabac.c
x264_051028/encoder/cavlc.c
x264_051028/encoder/encoder.c
x264_051028/encoder/eval.c
x264_051028/encoder/macroblock.c
x264_051028/encoder/macroblock.h
x264_051028/encoder/me.c
x264_051028/encoder/me.h
x264_051028/encoder/ratecontrol.c
x264_051028/encoder/ratecontrol.h
x264_051028/encoder/rdo.c
x264_051028/encoder/set.c
x264_051028/encoder/set.h
x264_051028/encoder/slicetype_decision.c
x264_051028/extras/
x264_051028/extras/getopt.c
x264_051028/extras/getopt.h
x264_051028/extras/stdint.h
x264_051028/Makefile
x264_051028/matroska.c
x264_051028/matroska.h
x264_051028/testing/
x264_051028/testing/checkasm.c
x264_051028/testing/edge-detec.c
x264_051028/testing/macroblock-dz.c
x264_051028/TODO
x264_051028/tools/
x264_051028/tools/.cvsignore
x264_051028/tools/avc2avi.c
x264_051028/tools/countquant_x264.pl
x264_051028/tools/Jamfile
x264_051028/tools/q_matrix_jvt.cfg
x264_051028/tools/x264-rd.sh
x264_051028/tools/xyuv.c
x264_051028/version.sh
x264_051028/vfw/
x264_051028/vfw/build/
x264_051028/vfw/build/cygwin/
x264_051028/vfw/build/cygwin/Makefile
x264_051028/vfw/build/win32/
x264_051028/vfw/build/win32/bin/
x264_051028/vfw/build/win32/bin/x264vfw.inf
x264_051028/vfw/build/win32/x264vfw.dsp
x264_051028/vfw/build/win32/x264vfw.dsw
x264_051028/vfw/codec.c
x264_051028/vfw/config.c
x264_051028/vfw/driverproc.c
x264_051028/vfw/driverproc.def
x264_051028/vfw/installer/
x264_051028/vfw/installer/win.bmp
x264_051028/vfw/installer/x264-conf.nsi
x264_051028/vfw/installer/x264vfw.ico
x264_051028/vfw/resource.h
x264_051028/vfw/resource.rc
x264_051028/vfw/w32api/
x264_051028/vfw/w32api/vfw.h
x264_051028/vfw/x264.bmp
x264_051028/vfw/x264vfw.h
x264_051028/x264.c
x264_051028/x264.h
Platform:   X86
System:     LINUX
avis input: no
mp4 output: no
pthread:    yes
vfw:        no
debug:      no
visualize:  no

You can run 'make' now.
rm -f .depend
( echo -n "`dirname common/mc.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/mc.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/predict.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/predict.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/pixel.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/pixel.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/macroblock.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/macroblock.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/frame.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/frame.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/dct.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/dct.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/cpu.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/cpu.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/cabac.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/cabac.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/common.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/common.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/mdate.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/mdate.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/csp.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/csp.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/set.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/set.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/quant.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/quant.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/analyse.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 encoder/analyse.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/me.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 encoder/me.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/ratecontrol.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 encoder/ratecontrol.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/set.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 encoder/set.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/macroblock.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 encoder/macroblock.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/cabac.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 encoder/cabac.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/cavlc.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 encoder/cavlc.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/encoder.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 encoder/encoder.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname encoder/eval.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 encoder/eval.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/i386/mc-c.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/i386/mc-c.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname common/i386/dct-c.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/i386/dct-c.c -MM -g0 ) 1>> .depend; ( echo -n "`dirname common/i386/predict.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 common/i386/predict.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname x264.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 x264.c -MM -g0 ) 1>> .depend;  ( echo -n "`dirname matroska.c`/" && gcc -Wall -I. -O4 -ffast-math -D__X264__ -DHAVE_MALLOC_H -DHAVE_MMXEXT -DHAVE_SSE2 -DARCH_X86 -DSYS_LINUX -DHAVE_PTHREAD=1 -s -fomit-frame-pointer -DHAVE_GETOPT_LONG=1 matroska.c -MM -g0 ) 1>> .depend;
nasm -f elf -o common/i386/dct-a.o common/i386/dct-a.asm
make: nasm: Command not found
make: *** [common/i386/dct-a.o] Error 127
ERROR during compilation or installation of X264
cleippi@FamilyComputer:~/Desktop/pspvc-install-0.2.1$ make
make: *** No targets specified and no makefile found.  Stop.
```

actually here is the whole thing

---

### Post by po0f on 2006-11-05
Fittersman,

Read my last post.

---

### Post by Fittersman on 2006-11-05
where can i get gtk+2.0 i found the other ones in symnatec advanced menu thing but the gtk+2.0 needs some other ones and that one needs some other ones and you can never get to the end of requirements (well i gave up) but is there like a package that will install all of them?

---

### Post by po0f on 2006-11-05
Fittersman,

Try this:
```
$ sudo aptitude install libgtk2.0-dev
```

---

### Post by taurus on 2006-11-05
The best way is to use the Search option in synaptic!  Just type in "gtk+" (without the quotes) and it will show you a long list of it...

---

### Post by Fittersman on 2006-11-05
ok i tried both suggestions but neither worked....(well they worked but not with the results i needed)

---

