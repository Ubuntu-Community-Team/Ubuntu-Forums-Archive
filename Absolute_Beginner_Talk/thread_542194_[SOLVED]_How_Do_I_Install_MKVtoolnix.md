---
title: "[SOLVED] How Do I Install MKVtoolnix ??"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-03
Hi there

I'm stuck installing this package on Feisty Fawn, can someone tell me what I need to do next?

Thanks :)

[IMG]http://i18.tinypic.com/62fcjt1.jpg[/IMG]

---

### Post by splintercellguy on 2007-09-03
When you want to execute a file in the local directory, you prefix the command with ./, for installing from tarball, you can:

./configure (and install any dependecies that are needed, then re-run)
make
sudo make install

or:

./configure
make
sudo checkinstall (if you have the checkinstall package installed)

The latter will allow you to create a deb package that you can install and manage.

---

### Post by chrome307 on 2007-09-03
Hi there

I get some error messages running the /.configure command 

```


user@user-ubuntu:~$ ls
cxoffice     klibido           My Music        NZB DOWNLOADS
Desktop      mkvtoolnix-2.1.0  My Pictures     Software
devede-3.01  My Documents      My Videos       Windows Apps
Examples     My Downloads      newspost-2.1.1  zd1211-firmware
user@user-ubuntu:~$ cd mkvtoolnix-2.1.0
user@user-ubuntu:~/mkvtoolnix-2.1.0$ ls
AUTHORS         configure     libmtxcommon.vcproj  mkvtoolnix-unicode.nsi
autogen.sh      configure.in  librmff              NEWS
autom4te.cache  contrib       Makefile.in          po
avilib-0.6.10   COPYING       mkinstalldirs        README
ChangeLog       debian        mkvextract.vcproj    README.Windows.txt
common.vcproj   doc           mkvinfo.vcproj       src
config.h.in     examples      mkvmerge.vcproj      tests
config.log      INSTALL       mkvtoolnix.nsi       TODO
config.msvc.h   install-sh    mkvtoolnix.sln


```

```


user@user-ubuntu:~/mkvtoolnix-2.1.0$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for ar... ar
checking for ld... ld
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
checking for inttypes.h... (cached) yes
checking for stdint.h... (cached) yes
checking for sys/types.h... (cached) yes
checking for vsscanf... yes
checking whether the byte order is big-endian... no
checking gcc version... 4.1.2
checking if being compiled with mingw32... no
checking for int64_t... yes
checking for uint64_t... yes
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for long long... yes
checking size of long long... 8
checking for PRId64 and PRIu64... yes
checking for posix_fadvise... yes
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo... yes
checking for ogg_sync_init in -logg... no
configure: error: Could not find the Ogg library
user@user-ubuntu:~/mkvtoolnix-2.1.0$ 



```

---

### Post by shirilover on 2007-09-03
An easier way would be
```

wget http://www.bunkus.org/gpg-pub-moritzbunkus.txt -O- | sudo apt-key add -

```
You can get the package by adding the following lines to your /etc/apt/sources.lst on your "Dapper Drake" installation:
```

deb http://www.bunkus.org/ubuntu/dapper/ ./
deb-src http://www.bunkus.org/ubuntu/dapper/ ./

```
and these are for "Edgy Eft":
```

deb http://www.bunkus.org/ubuntu/edgy/ ./
deb-src http://www.bunkus.org/ubuntu/edgy/ ./

```
and "Feisty Fawn":
```

deb http://www.bunkus.org/ubuntu/feisty/ ./
deb-src http://www.bunkus.org/ubuntu/feisty/ ./

```

Then,
```

sudo aptitude update
sudo aptitude install mkvtoolnix-mb

```

or you can grab the version that's in the universe repo.

---

### Post by chrome307 on 2007-09-04
Thanks for the help ....... but I still have problems with this application ....... also I can find an executable file to run it either :confused:

[IMG]http://i19.tinypic.com/4yk21j8.jpg[/IMG]

[IMG]http://i2.tinypic.com/6c4vrfc.jpg[/IMG]

[IMG]http://i13.tinypic.com/61vc17l.jpg[/IMG]

---

### Post by shirilover on 2007-09-04
The executable is mmg(MKVMergeGUI) which uses mkvmerge.
It should be in /usr/bin.

---

### Post by chrome307 on 2007-09-04
Thanks for the advice and support :)

The *.EXE works ............ not sure why I got the error messages .... these know popup each time I open up Synaptic Package Manager.

Should I remove the entries listed above ??

[IMG]http://i5.tinypic.com/4vfdx6b.jpg[/IMG]

---

### Post by shirilover on 2007-09-04
OK, down load the public key -> [http://www.bunkus.org/gpg-pub-moritzbunkus.txt](http://www.bunkus.org/gpg-pub-moritzbunkus.txt)
Open synaptic, go to Settings -> Repositories
Click on the Authentication tab
click the Import Key File ... button
browse to the file you saved in the first step and click OK.
the problem should go away.

---

### Post by chrome307 on 2007-09-04
Thank You again :)

It worked with the key file you posted

---

### Post by iSplicer on 2008-04-30
This thread helped me a lot. Thanks

---

