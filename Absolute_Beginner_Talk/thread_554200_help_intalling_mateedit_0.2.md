---
title: "help intalling mateedit 0.2"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by animefan61 on 2007-09-18
I installed mateedit to my computer using add/remove program and it won't work. I went to the mateedit 0.2 website and downloaded mateedit 0.2.  It's a tar.bz2. I unpackaged it, moved it to my home folder and configured it. Now it won't let me install or makefile the program, and it won't run.  Can anyone tell me what I need to do? Thanks in advance.

---

### Post by jnorth on 2007-09-18
Which version did you install from the repository?  Also, what is failing?

Try a ```
sudo apt-get update
sudo apt-get install mateedit
```

You must forgive me if you have already tried this, but since this is the beginner forum I try to provide more detail as opposed to less.

---

### Post by animefan61 on 2007-09-18
jnorth I just tried your suggestion and  it didn't work. The version I have installed is the one that came with Ubuntu, but I downloaded the mateedit 0.2 and I can't install it.  It configured, but it won't install.

---

### Post by animefan61 on 2007-09-19
Please, can anybody help me?

---

### Post by jnorth on 2007-09-19
What error are you getting?  Can you copy and paste the output of both the configure command, and the output of the make command?

---

### Post by animefan61 on 2007-09-19
I installed mateedit with add/remove. It installed, but when I go to accessories and click mateedit a window will open but it won't let me do anything. I downloaded mateedit-0.2 and extracted it. I moved the folder to my home directory. I open a terminal and  change directory to mateedit-0.2 I type ./configure and it configures. I type ./install and it says there's no such file or directory. I type ./make and it tells me there's no such file or directory, but when I open the folder those files are there. Here's what my terminal looks like:

linda@linda-desktop:~$ cd mateedit-0.2
linda@linda-desktop:~/mateedit-0.2$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
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
checking whether g++ supports -Wmissing-format-attribute... no
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wnon-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
linda@linda-desktop:~/mateedit-0.2$ ./make
bash: ./make: No such file or directory
linda@linda-desktop:~/mateedit-0.2$

---

### Post by animefan61 on 2007-09-20
Can anyone help me please?

---

### Post by animefan61 on 2007-09-20
Help please, anybody.

---

### Post by animefan61 on 2007-09-21
Will anybody help me?

---

### Post by animefan61 on 2007-09-21
If there isn't anything I can do, would someone please tell me?

---

### Post by animefan61 on 2007-09-24
Will sombody, anybody please help me, or tell me that I can't be helped.

---

### Post by Maestro23 on 2007-09-24
You are compiling something from source.  Do you have build-essential installed?

> sudo apt-get install build-essential

Also, check the README/INSTALL doc for the program.  It should give instructions and tell you any other programs it might require.

---

### Post by animefan61 on 2007-09-24
Thank you so much Maestro23, I did what you said. Now I have a new problem. It configured, but when I typed make, here's what I got:

linda@linda-desktop:~/mateedit-0.2$ make
make  all-recursive
make[1]: Entering directory `/home/linda/mateedit-0.2'
Making all in doc
make[2]: Entering directory `/home/linda/mateedit-0.2/doc'
Making all in .
make[3]: Entering directory `/home/linda/mateedit-0.2/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/linda/mateedit-0.2/doc'
Making all in en
make[3]: Entering directory `/home/linda/mateedit-0.2/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/linda/mateedit-0.2/doc/en'
make[2]: Leaving directory `/home/linda/mateedit-0.2/doc'
Making all in po
make[2]: Entering directory `/home/linda/mateedit-0.2/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/linda/mateedit-0.2/po'
Making all in src
make[2]: Entering directory `/home/linda/mateedit-0.2/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT main.o -MD -MP -MF ".deps/main.Tpo" \
          -c -o main.o `test -f 'main.cpp' || echo './'`main.cpp; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; \
        else rm -f ".deps/main.Tpo"; exit 1; \
        fi
message.h:182: error: ‘QBuffer’ has not been declared
message.h:379: warning: ‘class MateEdit::Client’ has virtual functions but non-virtual destructor
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/linda/mateedit-0.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/linda/mateedit-0.2'
make: *** [all] Error 2
linda@linda-desktop:~/mateedit-0.2$ 

How do I declare my QBuffer?

---

### Post by animefan61 on 2007-09-25
Can someone help me please?

---

### Post by animefan61 on 2007-09-25
I know someone can help.

---

### Post by animefan61 on 2007-09-26
Someone please help, I'm trying to be patient, but I am getting frustrated.

---

### Post by animefan61 on 2007-09-27
Please, won't someone help me?:(:cry:

---

### Post by animefan61 on 2007-09-27
I really want to get this program running, if nobody can help me, can someone suggest another collabortive editor program?

---

