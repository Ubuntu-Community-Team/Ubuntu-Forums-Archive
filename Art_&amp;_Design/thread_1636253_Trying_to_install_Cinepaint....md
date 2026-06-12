---
title: "Trying to install Cinepaint..."
date: 2010-12-02
forum: Art &amp; Design
---

### Post by -nat- on 2010-12-02
I'm trying to install Cinepaint on Ubuntu 10.10, but am not having any luck. Is it even possible to get running?

Installing from source, I am able to ./configure successfully, but 'make' gives: ```
make: *** No targets.  Stop.
```

---

### Post by jcolyn on 2010-12-02
Why not install via package manager such as synaptic? It's in the repos.

---

### Post by -nat- on 2010-12-02
> **jcolyn said:**
> Why not install via package manager such as synaptic? It's in the repos.

Really? I can't see it when searching in Synaptic.
I tried installing via an RPM (converted to a DEB with alien), but when I try to run it from terminal I get:

```
cinepaint: error while loading shared libraries: liboyranos.so.0.1.7: cannot open shared object file: No such file or directory
```

---

### Post by -nat- on 2010-12-02
Got it working. I installed oyranos from the getdeb repos, but it was version 0.1.9. I then went into /usr/lib/ and made a link to 'liboyranos.so.0.1.9' but named it 'liboyranos.so.0.1.7'

---

### Post by gustavomazza on 2010-12-18
I'm still trying to figure this install, downloaded cinepaint-0.22-1 and  extracted to my /home directory, in a subdirectory /cinepaint-0.22-1

The OS is ubuntu 10.10

Followed the text in
[http://cinepaint.bigasterisk.com/SourceTarball](http://cinepaint.bigasterisk.com/SourceTarball) 

 after the ./configure command received this log

--------------------------------------------------------
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether build environment is sane... yes
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
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
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking whether ln -s works... yes
checking build system type... x86_64-unknown-linux
checking host system type... x86_64-unknown-linux
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check

------------------------------------------

looks there is a lot of C++ G++ compilers that failed, getting them will solve this ?

---

### Post by graphius on 2011-01-16
I have basically given up on Cinepaint in Ubuntu, unless anyone has any simple suggestions...

---

### Post by gustavomazza on 2011-01-17
> **graphius said:**
> I have basically given up on Cinepaint in Ubuntu, unless anyone has any simple suggestions...

So do I, tried a lot of things and nothing worked.

---

### Post by mark.0 on 2011-07-03
> **graphius said:**
> I have basically given up on Cinepaint in Ubuntu, unless anyone has any simple suggestions...

Same here. This is a real shame, the 0.22 source doesn't even compile with make in my experiences. The source isn't being very well maintained I attempted to fix a missing <cstring> include in br_Image.cpp and so on but continued to run into other compile errors. The cinepaint website doesn't appear to be maintained still either - it's an out of the box wordpress installation that hasn't been touched for almost a year now... Has the cinepaint project been abandoned? I've heard rumors of a developer working on debian packaging, but all these rumors are dated from like a year ago.

This is a real shame, cinepaint was the best thing for 16bit processing on ubuntu :(

---

### Post by graphius on 2011-07-03
I had to ... gasp.... install photoshop in wine....

Hopefully GIMP improves over the next while to support larger bit depth, among other things...

---

### Post by MooseDog on 2011-07-03
fwiw, i found

cinepaint_0.24-cvs_i386.deb

i totally forget where, and it installed rather automagically, as a deb should.

---

### Post by prokoudine on 2011-07-04
> **mark.0 said:**
> Same here. This is a real shame, the 0.22 source doesn't even compile with make in my experiences.

The more or less up to date code is here:

[http://www.oyranos.org/scm?p=cinepaint.git;a=summary](http://www.oyranos.org/scm?p=cinepaint.git;a=summary)

It's not the official Cinepaint, just a silent fork by its former co-developer.

---

