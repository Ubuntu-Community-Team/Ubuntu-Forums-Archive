---
title: "gaim - otr"
date: 2005-07-29
forum: Apple PPC Users
---

### Post by dorjee on 2005-07-29
Hi!
Ive tried to intstall the gaim-otr plugin
([http://www.cypherpunks.ca/otr/](http://www.cypherpunks.ca/otr/))
But cant get it to work properly...
Ive tried to convert the rpm package with alien with no succes and also tried to install it with a .deb package...
Is says that it need some liberary but that liberarys version number is x.x.xx+ubuntu something... and the package cant install with that version...
Help! I REALLY need this plugin!

Many thanks, Dorjee

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=dorjee]
Ive tried to convert the rpm package with alien with no succes and also tried to install it with a .deb package...
Is says that it need some liberary but that liberarys version number is x.x.xx+ubuntu something... and the package cant install with that version...
[/QUOTE]

What about compiling from source?

---

### Post by pestilence4hr on 2005-07-29
[QUOTE=dorjee]Hi!
Ive tried to intstall the gaim-otr plugin
([http://www.cypherpunks.ca/otr/](http://www.cypherpunks.ca/otr/))
But cant get it to work properly...
Ive tried to convert the rpm package with alien with no succes and also tried to install it with a .deb package...
Is says that it need some liberary but that liberarys version number is x.x.xx+ubuntu something... and the package cant install with that version...
Help! I REALLY need this plugin!

Many thanks, Dorjee[/QUOTE]
 As a side note, why not use gaim-encryption?  That is apt-get'able.

---

### Post by dorjee on 2005-07-29
I dont want to use gaim-encryption becaus my friends isnt using (and cant) use that...
(they run Adium on mac).

Im still a noob on linux (installed it this week, and love it btw) så I dont know any comandos or anything like that. (I know windows and mac pretty well, but linux is another thing...)

So, how do I compile the package?

---

### Post by pierba on 2005-07-30
You must download package .tar.gz or .tar.bz2

type on shell:
tar zxvf /directory/whereis/package.tar.gz
or
tar xjvf /directory/whereis/package.tar.bz2

read the file README or INSTALL or BUILD, in the directory created in your home and you find all the explanation to compile.

Pietro

---

### Post by kkass on 2005-08-08
Hey I don't know if you managed to get OTR working or not, but here is what I did to get it working.

First download libotr1_2.0.2-1_i386.deb and libotr1-bin_2.0.2-1_i386.deb from the following source. [http://fatboy.umng.edu.co/debian/pool/main/libo/libotr/](http://fatboy.umng.edu.co/debian/pool/main/libo/libotr/) 

Now install the packages.
sudo dpkg --force-depends -i Desktop/libotr1_2.0.2-1_i386.deb
sudo dpkg -i Desktop/libotr1-bin_2.0.2-1_i386.deb

(I included the force-depends option on the first because they both depended on the other, so neither would install.)  Now download and install the gaim plugin.

sudo dpkg -i Desktop/gaim-otr_2.0.2-1_i386.deb

Once you restart gaim and confifigure OTR, everything should be working.

Hope this helps.

---

### Post by dorjee on 2005-08-14
Hi!
I havnt tried to install OTR yet, (but I will try tonight or tomorrow).
I saw that the -deb package is for intel-rocessors, can I still install it on my PPC or do I need to compile it?

---

### Post by kkass on 2005-08-15
That I do not know.

You can try installing it anyway, it should not break anything if it doesnt work.  My guess would be that is doesnt really matter.  First try searching for PPC versions of the files though.

---

### Post by dorjee on 2005-08-17
Hi!
I cant understand how to compile...
I have downloaded the source files and uncompressed them.
But how to do now?
I have tried to understand the INSTALL file, but no success...
Heres what it says:




REQUIREMENTS

To compile the OTR library and toolkit, you'll need at least:
 - libgpg-error 1.0  [[ftp://ftp.gnupg.org/gcrypt/libgpg-error/]](ftp://ftp.gnupg.org/gcrypt/libgpg-error/])
 - libgcrypt 1.2.0   [[ftp://ftp.gnupg.org/gcrypt/libgcrypt/]](ftp://ftp.gnupg.org/gcrypt/libgcrypt/])

If you install these with a package manager, you'll probably need the
-dev or -devel versions of the packages.

On Fedora, these packages are:
    libgpg-error-devel libgcrypt-devel

On Debian (testing or unstable), they are:
    libgpg-error-dev libgcrypt11-dev

COMPILING

If you're got a CVS copy, you will need to regenerate the configure
script using:

    autoreconf -s -i

Once you have the configure script (which comes with the source
deistribution), run it with the "--with-pic" option, as well as any
other options that may be necessary for your system.  Some examples:

Linux:
    ./configure --with-pic --prefix=/usr --mandir=/usr/share/man

NETBSD:
    CPPFLAGS="-I/usr/pkg/include" LDFLAGS="-R/usr/pkg/lib -L/usr/pkg/lib" \
	./configure --with-pic --prefix=/usr/pkg

mingw cross-compiler from Debian Linux:
    ./configure --with-pic --build=`./config.guess` --host=i586-mingw32msvc \
	--prefix=/usr/i586-mingw32msvc

Once the configure script writes a Makefile, you should be able to just
run "make".

INSTALLATION

You should be able to simply do "make install".  If you want to install
somewhere other than / (this is useful for package creators), use
something like "make DESTDIR=/path/to/install/to install".

---

### Post by kkass on 2005-08-17
OK, first you want to install gcc some other development packages.  It is easiest if you use synaptic.  You can browse to the development section and select all the packages you need.  (The two packages you mentioned are available here.)

Now change to the directory where the source is located.  Then run the configure script.

```
$cd /home/{user name}/libotr-2.0.2
$./configure
```

Hopefully this run through just fine.  Read over the output and make sure it is not complaining about dependencies.  If it is, try to install them from synaptic.

Now run make.

```
$make
```

So long as this does not halt with errors you should be ok, it is not very informative about telling you that everything completed correctly.

Now install the library.

```
$sudo make install
```

The library should be ready to use.  Now you just have to install the GAIM plugin.

---

### Post by dorjee on 2005-08-18
Hi!
When I ran the ./configure script it reported the following error:

configure: error: libgcrypt 1.2.0 or newer is required.

But in synaptic it says that I have libgcrypt11 1.2.0-11 installed.
(and that is the only libcrypt in the database that has a version number with 1.2.0 or higher...)

How to do to make it work?

---

### Post by kkass on 2005-08-18
Also install libgcrypt11-dev.

---

### Post by dorjee on 2005-08-19
Hi!
Thank you for everything. Now I have manage to install "libotr" from source (and also learned someting about linux)

But when I tried to install gaim-otr from source It reported an error.
Firest I ran ```
cd /home/name/gaim-otr-2.0.2
```
and then ```
./configure
```
so far everything whent smooth...
Now I ran ```
make -f Makefile.mingw
``` as the INSTALL file said I should.
When I ran that the following error was reported:

```
~/gaim-otr-2.0.2$ make -f Makefile.mingw
i586-mingw32msvc-gcc -g -Wall -I/usr/include/gaim `pkg-config --cflags glib-2.0 gtk+-2.0` -I/usr/i586-mingw32msvc/include  -DUSING_GTK -DGAIM_PLUGINS -DGAIM_OTR_VERSION=\"2.0.2\"   -c -o otr-plugin.o otr-plugin.c
/bin/sh: i586-mingw32msvc-gcc: command not found
make: *** [otr-plugin.o] Fel 127
```

How do I install this thing....

---

### Post by kkass on 2005-08-22
Sorry, I was out of town this weekend!

Try calling make without the included makefile.  The configure script should have created a custom makefile for your system.

```
make
```

---

### Post by dorjee on 2005-08-22
Hi!
I tried that too and then It installed ok, but the plugin didnt turn up in GAIM...is there a way around this?

---

### Post by kkass on 2005-08-22
Ok, double check all the output and make sure that there is no hidden error.  (I have found sometimes that the compile or configure step will complain about a dependency, but still complete and appear to be ok.)

You did exit and restart Gaim correct?

I will try compiling and installing from source later.

---

### Post by kkass on 2005-11-17
Did you ever get this to work?  I forgot to go back and check the build.  One thing you can try thogh is to set the prefix to /usr.  I think gaim looks for the plugins in /usr/lib, and the default install prefix may be /usr/local/lib.

```

./configure --prefix=/usr
make
sudo make install

```

---

### Post by dguido on 2006-01-19
or you could just install gaim-otr...?

---

