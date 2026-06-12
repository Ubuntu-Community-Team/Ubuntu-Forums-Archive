---
title: "Tangerine Daap"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by that guy on 2007-01-15
Hello,

Can anyone put together a quick HOWTO on installing Tangerine on Edgy?  

Sad to say, but I have no idea how to compile a program from source.:-k 

Here is the website:

[http://www.snorp.net/log/tangerine/]("http://www.snorp.net/log/tangerine/")

Thanks

---

### Post by Buck2348 on 2007-01-16
I'm a relative newbie, and I can't go very far toward answering your question.  From what I have seen and experienced, the main problem with installing from source is satisfying dependencies, that is other software that the program you're installing has to have to run.  The general method for installing from source is 
1.  Extract files from the tar.gz.  I just right-click on it and select "extract here."  (This is on the desktop usually.)  You'll get an ordinary folder with the same name but without the "tar.gz."  cd into that folder in the terminal e.g.  code:  user@host:~$ cd Desktop/tangerine-0.3.0.

2.  Configure--:       code: ./configure     This executes the configure file in the package folder.

3.  Make--:               code: make           Compiles the code, I guess.

4.  Install--:            code: sudo make install

I just tried to install tangerine.  It went quite a ways on configure, then stopped with the line:
configure: error: Can not find "gmcs" in your PATH
Of course I have no idea what gmcs is or where it might be found.

There was no information that a quick look could discover on the tangerine site about what the program's dependencies are or other help for installing it.

I hope someone who knows more than I do will post a better answer in this thread--I'd like to know more myself.

Regards,
Buck

---

### Post by aamukahvi on 2007-05-04
Hi. You can get gmcs by installing it: In synaptic search for gmcs, there should be only one package.

I'm having trouble with this too:
```
@gutsy:~/src/tangerine-0.3.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

config.log:
```
------------------------8<-----------------------

configure:2533: $? = 0
configure:2535: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070429 (prerelease) (Ubuntu 4.1.2-5ubuntu2)
configure:2538: $? = 0
configure:2540: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:2543: $? = 1
configure:2566: checking for C compiler default output file name
configure:2569: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2572: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "tangerine"
| #define VERSION "0.3.0"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2611: error: C compiler cannot create executables
See `config.log' for more details.

------------------------8<-----------------------

```
I've no idea where to get **crtl.o**.

---

### Post by tmmuk on 2007-05-07
Hi, I managed to get this working on Feisty (64bit, should work on 32bit)

1. GET IT - download the latest source file: [http://www.snorp.net/files/tangerine/tangerine-0.3.0.tar.gz](http://www.snorp.net/files/tangerine/tangerine-0.3.0.tar.gz) 

2. EXTRACT IT - right click on the file you downloaded and click "Extract Here"

3. OPEN A TERMINAL and then type
```
cd /path/to/where/you/extracted/it
``` In my case, I typed:
```
cd ~/Desktop/tangerine-0.3.0/
```

4. FIX DEPENDENCIES - I had two required packages missing, you should get these if you don't already have them: 
```
sudo aptitude install mono-gmcs libavahi1.0-cil

```

5. INSTALL - then you just need to run
```
./configure
```
```
make
```
```
sudo make install
```

You should get a new launcher "Tangerine Music Sharing" under Accessories on the main menu. Run it, tick the box to enable sharing and pick a music source

Works for me...

---

### Post by aamukahvi on 2007-05-08
I have done all that but it still complains when I run ./configure:
```
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

---

### Post by mrashley on 2008-01-26
I figured out as far the instructions flowed on my own, but the make fails.

The ./configure stage gave me.

```
 tangerine prefix:    htpc@home-theatre:~/Desktop/tangerine-0.3.0$ ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
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
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether to enable maintainer-specific portions of Makefiles... no
checking for mono... /usr/bin/mono
checking for gmcs... /usr/bin/gmcs
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for AVAHI... yes
checking for GTK_SHARP... yes
checking for GLADE_SHARP... yes
checking for BEAGLE... checking for IPOD_SHARP... checking for GLIB_SHARP... yes
checking for muine... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating deps/Makefile
config.status: creating deps/daap-sharp/Makefile
config.status: creating deps/taglib-sharp/Makefile
config.status: creating icons/Makefile
config.status: creating src/Makefile
config.status: creating plugins/Makefile
config.status: creating plugins/file/Makefile
config.status: creating plugins/ipod/Makefile
config.status: creating plugins/beagle/Makefile
config.status: creating plugins/session/Makefile
config.status: creating plugins/banshee/Makefile
config.status: creating plugins/rhythmbox/Makefile
config.status: creating plugins/amarok/Makefile
config.status: creating plugins/muine/Makefile
config.status: creating plugins/muine/MuineDatabase.cs
config.status: creating tangerine.pc
config.status: executing depfiles commands

/usr/local
     iPod plugin:    no
   Beagle plugin:    no
    Muine plugin:    no
        Zeroconf:    Avahi
```

While the make stage gave me

```
htpc@home-theatre:~/Desktop/tangerine-0.3.0$ make
Making all in icons
make[1]: Entering directory `/home/htpc/Desktop/tangerine-0.3.0/icons'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/htpc/Desktop/tangerine-0.3.0/icons'
Making all in deps
make[1]: Entering directory `/home/htpc/Desktop/tangerine-0.3.0/deps'
Making all in daap-sharp
make[2]: Entering directory `/home/htpc/Desktop/tangerine-0.3.0/deps/daap-sharp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/htpc/Desktop/tangerine-0.3.0/deps/daap-sharp'
Making all in taglib-sharp
make[2]: Entering directory `/home/htpc/Desktop/tangerine-0.3.0/deps/taglib-sharp'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/htpc/Desktop/tangerine-0.3.0/deps/taglib-sharp'
make[2]: Entering directory `/home/htpc/Desktop/tangerine-0.3.0/deps'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/htpc/Desktop/tangerine-0.3.0/deps'
make[1]: Leaving directory `/home/htpc/Desktop/tangerine-0.3.0/deps'
Making all in src
make[1]: Entering directory `/home/htpc/Desktop/tangerine-0.3.0/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/htpc/Desktop/tangerine-0.3.0/src'
Making all in plugins
make[1]: Entering directory `/home/htpc/Desktop/tangerine-0.3.0/plugins'
Making all in file
make[2]: Entering directory `/home/htpc/Desktop/tangerine-0.3.0/plugins/file'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/htpc/Desktop/tangerine-0.3.0/plugins/file'
Making all in ipod
make[2]: Entering directory `/home/htpc/Desktop/tangerine-0.3.0/plugins/ipod'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/htpc/Desktop/tangerine-0.3.0/plugins/ipod'
Making all in beagle
make[2]: Entering directory `/home/htpc/Desktop/tangerine-0.3.0/plugins/beagle'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/htpc/Desktop/tangerine-0.3.0/plugins/beagle'
Making all in session
make[2]: Entering directory `/home/htpc/Desktop/tangerine-0.3.0/plugins/session'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/htpc/Desktop/tangerine-0.3.0/plugins/session'
Making all in banshee
make[2]: Entering directory `/home/htpc/Desktop/tangerine-0.3.0/plugins/banshee'
/usr/bin/gmcs -r:/usr/lib/cli/avahi-sharp-1.0/avahi-sharp.dll   -target:library -out:tangerine-banshee.dll ./BansheePlugin.cs \
	-r:../../deps/daap-sharp/daap-sharp.dll -r:../../deps/Nini.dll -r:../../deps/log4net.dll -r:../../src/tangerine.dll -r:System.Data -r:Mono.Posix -r:Mono.Data.SqliteClient
error CS0006: cannot find metadata file `Mono.Data.SqliteClient'
Compilation failed: 1 error(s), 0 warnings
make[2]: *** [tangerine-banshee.dll] Error 1
make[2]: Leaving directory `/home/htpc/Desktop/tangerine-0.3.0/plugins/banshee'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/htpc/Desktop/tangerine-0.3.0/plugins'
make: *** [all-recursive] Error 1

```

Does that give anyone a hint as to what I might be missing or doing wrong?

thanks :)

---

### Post by mrashley on 2008-01-26
Solved! 

```
sudo apt-get install libmono-sqlite2.0-cil

```

...will fix that error.

---

### Post by swhitney2003 on 2008-02-01
When I look at another computer running itunes I see two of my computer. I checked running processes in ubuntu and tangerine is running twice. why is this... can i fix it?

---

### Post by jackocleebrown on 2008-05-09
You may also need to install the package "libsm-dev"

Cheers, Jack.

---

### Post by jackocleebrown on 2008-05-09
The reason that you end up with two tangerines running at once is that the tangerine deamon is run when you login to the computer but remains running after you logout. If you login and then logout and login again you will end up with two copies running.

Instead of this you could run tangerine on startup so that you do not have to login to get it to work:

1) under "system"-"preferences"-"sessions" find the entry for tangerine in the "startup programs" tab and remove it (on my system it was called "unknown" or similar)

2) download attached zip, unzip to retrieve script inside. edit the script and change the username to your username (so that tangerine uses your preferences from the gui setup tool)

3) copy the script to /etc/init.d and run "sudo chmod a+x /etc/init.d/tangerine" and then "sudo update-rc.d tangerine defaults"

Done! will run on next boot.

Cheers, Jack.

---

### Post by IMB951 on 2008-06-23
The write error still hasn't been solved for me.  Tried everything in this thread, no luck.  Running 8.04

---

### Post by IMB951 on 2008-06-24
bump

---

### Post by jackocleebrown on 2008-06-26
Sorry IMB951,
What write error are you talking about??

---

### Post by IMB951 on 2008-06-26
I get this error when running ./config 

checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by jackocleebrown on 2008-06-27
Hi IMB951,

Try this:

```

sudo apt-get install libc6-dev
```

Actually I have just uninstalled tangerine from a couple of computers. I found that it did not cope well with tags or large music libraries, I've been using mt-daapd which is in the repositories and works really well.

Hope this helps, Jack.

---

### Post by IMB951 on 2008-06-30
That solved my issue.  Thanks!

---

