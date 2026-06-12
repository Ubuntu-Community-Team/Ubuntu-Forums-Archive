---
title: "compiling issues"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Hawk__0 on 2007-03-30
Is it normal in linux to have a lot of compiling issues?
for example, i downloaded 2 game: open duke, and unreal tournament clone for linux.

both of them wouldn't compile... C compiler returned errors.

then just today i downloaded "ktorrent", a utorrent clone, and i get this:


```
sgregory@sgregory-desktop:~/Desktop/ktorrent-2.1.2$ ./configure checking build system type... i686-pc-linux-gnulibc1 checking host system type... i686-pc-linux-gnulibc1 checking target system type... i686-pc-linux-gnulibc1 checking for a BSD-compatible install... /usr/bin/install -c checking for -p flag to install... yes checking whether build environment is sane... yes checking for gawk... no checking for mawk... mawk checking whether make sets $(MAKE)... yes checking for kde-config... /usr/bin/kde-config checking where to install... /usr (as returned by kde-config) checking for style of include used by make... GNU checking for gcc... gcc checking for C compiler default output file name... configure: error: C compiler cannot create executables See `config.log' for more details.

```

what gives?

---

### Post by dstew on 2007-03-30
Have you installed the build-essentials package from Synaptic? It contains the necessary compilers and libraries.

---

### Post by taurus on 2007-03-30
You need the build-essential package.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by Hawk__0 on 2007-03-30
ok thanks, but now i get this:
```

checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!

```

isnt X something to do with video?  i remember i had some similar issue when i tried to install nvidias drivers

---

### Post by taurus on 2007-03-30
You also need the dev package of xorg.

```
sudo aptitude install xorg-dev
```

---

### Post by Hawk__0 on 2007-03-30
thanks, that definitely did the trick.
why can i not install it now, though?

```
sgregory@sgregory-desktop:~/Desktop/ktorrent-2.1.1$ dir
acinclude.m4  config.log        COPYING-DOCS        libtool      stamp-h.in
aclocal.m4    configure         doc                 Makefile.am  subdirs
admin         configure.files   Doxyfile            Makefile.in  templates
apps          configure.in      estimation-scripts  NEWS         TODO
AUTHORS       configure.in.bot  INSTALL             plugins      translations
ChangeLog     configure.in.in   ktorrent.kdevelop   README       utests
config.h.in   COPYING           libktorrent         scripts
sgregory@sgregory-desktop:~/Desktop/ktorrent-2.1.1$ make
make: *** No targets specified and no makefile found.  Stop.
sgregory@sgregory-desktop:~/Desktop/ktorrent-2.1.1$ make install
make: *** No rule to make target `install'.  Stop.
sgregory@sgregory-desktop:~/Desktop/ktorrent-2.1.1$ 
```

---

### Post by bodhi.zazen on 2007-03-30
> **Hawk__0 said:**
> thanks, that definitely did the trick.
why can i not install it now, though?

```
sgregory@sgregory-desktop:~/Desktop/ktorrent-2.1.1$ dir
acinclude.m4  config.log        COPYING-DOCS        libtool      stamp-h.in
aclocal.m4    configure         doc                 Makefile.am  subdirs
admin         configure.files   Doxyfile            Makefile.in  templates
apps          configure.in      estimation-scripts  NEWS         TODO
AUTHORS       configure.in.bot  INSTALL             plugins      translations
ChangeLog     configure.in.in   ktorrent.kdevelop   README       utests
config.h.in   COPYING           libktorrent         scripts
sgregory@sgregory-desktop:~/Desktop/ktorrent-2.1.1$ make
make: *** No targets specified and no makefile found.  Stop.
sgregory@sgregory-desktop:~/Desktop/ktorrent-2.1.1$ make install
make: *** No rule to make target `install'.  Stop.
sgregory@sgregory-desktop:~/Desktop/ktorrent-2.1.1$ 
```

Start with ./configure
make
checkinstall

You will need to install checkinstall as well ...

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

Why not ```
sudo aptitude install ktorrent
``` ??

---

### Post by Hawk__0 on 2007-03-30
i didnt know you could do that... i dont really understand how this aptitude and apt-get stuff works... i know it downloads off the internet, but how does it work? is everything up there? liek if i wanted to get openduke, all i would have to do is sudo aptitude install openduke???

---

### Post by bodhi.zazen on 2007-03-30
> **Hawk__0 said:**
> i didnt know you could do that... i dont really understand how this aptitude and apt-get stuff works... i know it downloads off the internet, but how does it work? is everything up there? liek if i wanted to get openduke, all i would have to do is sudo aptitude install openduke???

lol , yep ...

You may need to enable a few repositories.

If you like apt-get and aptitude wait till you see synaptic :lolflag:

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

