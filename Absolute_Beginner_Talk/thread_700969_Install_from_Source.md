---
title: "Install from Source?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-02-18
In an effort to install AOL broadband on my computer (NOT for me, its for my mom, I hate the program), I am trying to install an OS X emulator on my computer (Wine wouldn't install the windows version of AOL), namely Mac on Linux, but I cannot seem to find the .deb files for it. So, I resorted to the source code (no real programming experience, so bear with me).

I unpacked the file in terminal using:

tar xvjf  mol-0.9.72.1.tar.bz2

which caused it to unpack. I then switched to the folder where they were unpacked to, then entered ./configure (trying to work my way to make and then make install). But I ran across this error:

==================================================
 Invoking autoheader and autoconf.
rm: cannot remove `config/configure/configure.in': Permission denied
mkdir: cannot create directory `config/configure': File exists
ln: creating symbolic link `config/configure/configure.in' to `../configure.in': File exists
./autogen.sh: 20: autoheader: not found
autoheader failed


Um, any suggestions?

---

### Post by Linux_Man on 2008-02-18
Run as root with "sudo" added to whatever command your using.

---

### Post by randy78 on 2008-02-18
Just cd to the directory and type make

I just did this and it worked, so you might be missing some dependencies...

Give it a shot...

I didn't  use ./configure or ./autogen...
just make ;)

Then of course, after make, you'll probably have to:
sudo make install

EDIT: Also, running as root when unnecessary can land you in hot water, so be sure to use SUDO and all its variants with extreme caution.

---

### Post by spacefreak86 on 2008-02-18
OKay, now I'm getting this error:

 Invoking autoheader and autoconf.
./autogen.sh: 20: autoheader: not found
autoheader failed

---

### Post by Linux_Man on 2008-02-18
do you have all your dependencies installed?

---

### Post by spacefreak86 on 2008-02-18
and then when I try sudo make install, I get this:

./autogen.sh
==================================================
 Invoking autoheader and autoconf.
./autogen.sh: 20: autoheader: not found
autoheader failed
make: *** [install-modules] Error 1

---

### Post by spacefreak86 on 2008-02-18
> **Linux_Man said:**
> do you have all your dependencies installed?

Not sure, I would guess not based on those errors. Where do I go to find them, and which ones do I need?

---

### Post by randy78 on 2008-02-18
It's in the BUILDING file...
Just double click it and it will open, with all the requirements listed.

---

### Post by spacefreak86 on 2008-02-18
Got it, had to install autoconf from Synaptic. Oh crap, now what do I do for the setup config that came up?

---

### Post by icechen1 on 2008-02-18
> **randy78 said:**
> 
sudo make install


doing sudo checkinstall will save you hours later if you want to remove the app because it will create a deb so you can uninstall it from synaptics.you need to install checkinstall from synaptics first though.

---

### Post by randy78 on 2008-02-18
> **spacefreak86 said:**
> Got it, had to install autoconf from Synaptic. Oh crap, now what do I do for the setup config that came up?

Hmm... 

I don't want to go that far on my machine, but I'm sure that if you read and follow the directions, you'll be fine ;)

---

### Post by spacefreak86 on 2008-02-18
Ok, so I got up to the sudo make step, and this is the error that came up:

sudo make
+ Entering scripts
+ Entering src
+ Entering lib
    Compiling    elfload.o           
In file included from elfload.c:34:
../../src/include/byteorder.h:27:31: error: cpu/mol_byteorder.h: No such file or directory
elfload.c: In function ‘fix_ehdr_byteorder’:
elfload.c:47: warning: implicit declaration of function ‘ld_be16’
elfload.c:49: warning: implicit declaration of function ‘ld_be32’
elfload.c:49: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:50: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:51: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:52: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:53: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c: In function ‘fix_phdr_byteorder’:
elfload.c:65: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:66: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:67: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:68: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:69: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:70: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:71: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:72: warning: dereferencing type-punned pointer will break strict-aliasing rules
make[2]: *** [../../obj-x86/build/src/lib/elfload.o] Error 1
make[1]: *** [sub-lib-all] Error 2
make: *** [sub-src-all] Error 2

---

### Post by randy78 on 2008-02-18
> **icechen1 said:**
> doing sudo checkinstall will save you hours later if you want to remove the app because it will create a deb so you can uninstall it from synaptics.you need to install checkinstall from synaptics first though.

True, but I was going for ease of installation here...
Checkinstall can fail, (as it has for me several dozen times) and then that'll probably just leave him confused even more!

:D

---

### Post by randy78 on 2008-02-18
No...

**JUST** make

Then sudo make install, or as Icechen1 suggested, sudo checkinstall... after you download the checkinstall package from Synaptic.

---

### Post by spacefreak86 on 2008-02-18
Okay, tried make, and this is what I got:

~/Desktop/mol-0.9.72.1$ make
ln: cannot remove `obj-x86/include/autoconf.h': Permission denied
make: *** [obj-x86/include/autoconf.h] Error 1

---

### Post by randy78 on 2008-02-18
Hmm...

Open a terminal and do this:
sudo apt-get install build-essential

then after that's installed, cd to the directory
in a terminal:
./configure
./autogen
make
sudo make install

or

./configure
skip ./autogen if it doesn't work
make
sudo make install

---

### Post by spacefreak86 on 2008-02-18
I was good until I hit make:

~/Desktop/mol-0.9.72.1$ sudo make
+ Entering scripts
+ Entering src
+ Entering lib
    Compiling    extralib.o          
    Compiling    llseek.o            
    Compiling    elfload.o           
In file included from elfload.c:34:
../../src/include/byteorder.h:27:31: error: cpu/mol_byteorder.h: No such file or directory
elfload.c: In function &#8216;fix_ehdr_byteorder&#8217;:
elfload.c:47: warning: implicit declaration of function &#8216;ld_be16&#8217;
elfload.c:49: warning: implicit declaration of function &#8216;ld_be32&#8217;
elfload.c:49: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:50: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:51: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:52: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:53: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c: In function &#8216;fix_phdr_byteorder&#8217;:
elfload.c:65: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:66: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:67: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:68: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:69: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:70: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:71: warning: dereferencing type-punned pointer will break strict-aliasing rules
elfload.c:72: warning: dereferencing type-punned pointer will break strict-aliasing rules
make[2]: *** [../../obj-x86/build/src/lib/elfload.o] Error 1
make[1]: *** [sub-lib-all] Error 2
make: *** [sub-src-all] Error 2

(I had to use sudo, it kept telling me permission denied)

---

### Post by randy78 on 2008-02-18
Also, if you are missing dependencies, then ./configure will list them when it is done checking for them, and from there you can just search for them in Synaptic.

---

### Post by spacefreak86 on 2008-02-18
> **randy78 said:**
> Also, if you are missing dependencies, then ./configure will list them when it is done checking for them, and from there you can just search for them in Synaptic.

No dependencies came up, it kept saying everything was ok when I ran ./configure

---

### Post by randy78 on 2008-02-18
> **spacefreak86 said:**
> No dependencies came up, it kept saying everything was ok when I ran ./configure

Did you install build-essential?

---

### Post by spacefreak86 on 2008-02-18
Yes, I did.

---

### Post by randy78 on 2008-02-18
Okay... one more time...

Open a terminal
type cd
press the SPACE bar once
left mouse-click on the folder once and drag it into the terminal
click once in the terminal
hit enter
type ./configure
after that completes, type ./autogen (if it doesn't work, then skip it)
type make
type sudo make install

These are the EXACT steps that I have taken, except for: sudo make install

Everything has worked flawlessly on my end.

You may want to try rebooting or logging out first (for the build-essential)
I am almost positive that you are missing some dependencies...

Let's keep trying!

---

### Post by spacefreak86 on 2008-02-18
bdizzle86@MINE:~$ cd '/home/bdizzle86/Desktop/mol-0.9.72.1'
bdizzle86@MINE:~/Desktop/mol-0.9.72.1$ ./configure
rm: cannot remove `config.log': Permission denied
./configure: 51: cannot create conf15105.sh: Permission denied
./configure: 51: cannot create conf15105.sh: Permission denied
chmod: cannot access `conf15105.sh': No such file or directory
./configure: line 42: conf15105.sh: Permission denied
./configure: line 43: conf15105.sh: Permission denied
chmod: cannot access `conf15105.sh': No such file or directory
mkdir: cannot create directory `conf15105.dir': Permission denied
./configure: line 497: conf15105.file: Permission denied
./configure: line 1385: config.log: Permission denied
./configure: line 1395: config.log: Permission denied
bdizzle86@MINE:~/Desktop/mol-0.9.72.1$

---

### Post by spacefreak86 on 2008-02-18
Edit: tried sudo ./configure, this is the output:

bdizzle86@MINE:~/Desktop/mol-0.9.72.1$ sudo ./configure
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking obstack.h usability... yes
checking obstack.h presence... yes
checking for obstack.h... yes
checking dependency style... new
checking for clearenv()... yes
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking for snd_pcm_open in -lasound... yes
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for working XDGA headers... no
checking whether XDGA workaround works... no
checking for m4... m4
checking for as... as
checking for strip... strip 
checking for ld... ld
checking for nm... nm
checking for objdump... objdump
checking for install... install
checking whether off_t is 64 bit... no
checking for broken syscall macro... yes
checking for uc_context.gregs... yes
checking for png_read_png in -lpng... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for -fno-stack-protector support... yes
checking for inflate in -lz... yes
configure: creating ./config.status
config.status: creating unconfig
config.status: creating Makefile.defs
config.status: creating config.h
config.status: config.h is unchanged
bdizzle86@MINE:~/Desktop/mol-0.9.72.1$

---

### Post by randy78 on 2008-02-18
Crazy...

Here is what mine looks like:

randy@Ubuntu:~/Desktop/mol-0.9.72.1$ ./configure
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for bison... bison -y
checking for flex... flex
checking lex output file root... lex.yy
checking lex library... -lfl
checking whether yytext is a pointer... yes
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking poll.h usability... yes
checking poll.h presence... yes
checking for poll.h... yes
checking obstack.h usability... yes
checking obstack.h presence... yes
checking for obstack.h... yes
checking dependency style... new
checking for clearenv()... yes
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking for snd_pcm_open in -lasound... no
checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... no
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for working XDGA headers... no
checking whether XDGA workaround works... no
checking for m4... m4
checking for as... as
checking for strip... strip 
checking for ld... ld
checking for nm... nm
checking for objdump... objdump
checking for install... install
checking whether off_t is 64 bit... no
checking for broken syscall macro... yes
checking for uc_context.gregs... yes
checking for png_read_png in -lpng... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for -fno-stack-protector support... yes
checking for inflate in -lz... yes
configure: creating ./config.status
config.status: creating unconfig
config.status: creating Makefile.defs
config.status: creating config.h
config.status: config.h is unchanged

-------------
I think that gcc is installed by default, but you might want to try:
sudo apt-get install gcc

---

### Post by randy78 on 2008-02-18
I'm curious as to why you are having to sudo ./configure...

As you can see in my post, that isn't the case, and honestly, I've never had to sudo to do that before!

I honestly think that we should hang on a little bit and wait for a senior member/moderator to come check this out.

---

### Post by spacefreak86 on 2008-02-18
Tried the gcc, it claims it is already installed and updated. But yeah, this is wierd.

---

### Post by 3rdalbum on 2008-02-18
Mac-On-Linux requires a PowerPC processor, which basically means that you need a pre-2006 Macintosh. If your computer can run Microsoft Windows, then you CANNOT run Mac-On-Linux.

---

### Post by spacefreak86 on 2008-02-18
Oh, ok. That solves that problem then. Okay, so then the next question. How do I get AOL 9.1 running on my computer for my mom to use (email and all that).

---

