---
title: "libsamplerate-0.1.2"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by lifemaximum on 2006-10-04
I was trying to install libsamplerate-0.1.2, so i configured it using ./configure, it worked fine, than i used make , and make check , so far no problem but when i tried make install i got :



-----------------------------------------------------------------
  libsamplerate-0.1.2 passed all tests.
-----------------------------------------------------------------
make[1]: Leaving directory `/home/faz/Desktop/libsamplerate-0.1.2/tests'
make[1]: Entering directory `/home/faz/Desktop/libsamplerate-0.1.2'
make[1]: Nothing to be done for `check-am'.
make[1]: Leaving directory `/home/faz/Desktop/libsamplerate-0.1.2'
[COLOR="Red"]faz@faz-laptop:~/Desktop/libsamplerate-0.1.2$ make install[/COLOR]
Making install in src
make[1]: Entering directory `/home/faz/Desktop/libsamplerate-0.1.2/src'
make[2]: Entering directory `/home/faz/Desktop/libsamplerate-0.1.2/src'
/bin/sh ../mkinstalldirs /usr/local/lib
 /bin/sh ../libtool --mode=install /usr/bin/install -c  libsamplerate.la /usr/local/lib/libsamplerate.la
/usr/bin/install -c .libs/libsamplerate.so.0.1.1 /usr/local/lib/libsamplerate.so.0.1.1
/usr/bin/install: cannot create regular file `/usr/local/lib/libsamplerate.so.0.1.1': Permission denied
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/faz/Desktop/libsamplerate-0.1.2/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/faz/Desktop/libsamplerate-0.1.2/src'
make: *** [install-recursive] Error 1



could someone help to install it ? that would be much apperciated thanks

---

### Post by think13 on 2006-10-04
You could simply install it using synaptic, just search for 'libsamplerate'.

Also instead of make install, try 
sudo make install

or
sudo make

---

### Post by ciscosurfer on 2006-10-04
Use checkinstall insead (it will create a package that can be removed easily if need be).  Download checkinstall via apt or your favorite package manager.  You general steps should be:
[COLOR=Red] sudo ./configure
sudo make
sudo checkinstall[/COLOR]

Also, it's a good idea to download [COLOR=Red]build-essential[/COLOR] ... it will greatly aid you (it's a metapackage that contains appropriate compilers, etc.)

---

### Post by lifemaximum on 2006-10-07
i tried to compile movie editor ? and i got this error? u know what i should do ?

i first used[COLOR="Red"] sudo ./configure[/COLOR] ....got it configured first ...than i tried [COLOR="Red"]sudo make[/COLOR] and that is where i got tat error?
[COLOR="Red"]

faz@faz-laptop:~/Desktop/openmovieeditor-0.0.20060901$ sudo make
make: *** No targets specified and no makefile found.  Stop.
[/COLOR]

---

