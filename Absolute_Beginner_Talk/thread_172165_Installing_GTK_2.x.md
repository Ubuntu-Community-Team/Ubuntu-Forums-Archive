---
title: "Installing GTK 2.x"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by n11 on 2006-05-08
Hi, I wanted to install snes9express. so i downloaded the tarball,extracted it ,went to the folder and typed "./configure".I am giving detailed steps because it is the first time i am compiling anything. I had earlier read some documentation and corectly installed "build-" something.I get the following output:

:~/My Documents/snes9express-1.42$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for gzopen in -lz... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking for stdlib.h... (cached) yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for unistd.h... (cached) yes
checking linux/joystick.h usability... yes
checking linux/joystick.h presence... yes
checking for linux/joystick.h... yes
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for mode_t... yes
checking for pid_t... yes
checking whether sys_siglist is declared... no
checking whether struct tm is in sys/time.h or time.h... time.h
checking whether closedir returns void... no
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking whether gcc needs -traditional... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for strftime... yes
checking for dup2... yes
checking for getcwd... yes
checking for localtime_r... yes
checking for memset... yes
checking for mkdir... yes
checking for putenv... yes
checking for realpath... yes
checking for rmdir... yes
checking for select... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strdup... yes
checking for strerror... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtol... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0...
The proper GTK development tools could not be found
GTK 2.x is required.

Any help is greatly appreciated.

---

### Post by Perfect Storm on 2006-05-08
you need to install libgtk2-dev

Normally when you compile and it says you're missing something, make sure you have the -dev package as well. It need the -dev's to build from.

Another good way when compiling is to read the readme.txt and/or whhat the say about building it from their homepage. If you want to tweak it run first ./configure --help it will lists all the flags etc.

---

### Post by sophtpaw on 2006-05-08
[QUOTE=Artificial Intelligence]you need to install libgtk2-dev

Normally when you compile and it says you're missing something, make sure you have the -dev package as well. It need the -dev's to build from.

Another good way when compiling is to read the readme.txt and/or whhat the say about building it from their homepage. If you want to tweak it run first ./configure --help it will lists all the flags etc.[/QUOTE]

Sorry, what is GTK2 ?

Been configuring and personalising my gnome look. Besides backgrounds i never knew to change anything else. 
Yesterday just learnt to change login page. I think that is called GDM themes?
I see on gnome-look.org also metacity, splashscreen and gtk1 and 2. I don't know what all these refer to

don't meanto hijack the thread. I hoped it'd be ok to ask here as i'm trying to learn more 

--
sophtpaw

---

### Post by n11 on 2006-05-08
Installed it and the "./configure" went smoothly. But when i try "make" i get: 

g++ -DHAVE_CONFIG_H -I. -I. -I.  -DS9XDATADIR=\"/usr/local/share/snes9express\"  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -g -O2 -c frend.cc
frend.cc: In function &#8216;std::string fr_syserr()&#8217;:
frend.cc:3115: error: &#8216;errno&#8217; was not declared in this scope
make: *** [frend.o] Error 1

I ignored it and tried "make install" but i got the same error.Any ideas?

---

### Post by Perfect Storm on 2006-05-08
[QUOTE=sophtpaw]Sorry, what is GTK2 ?

Been configuring and personalising my gnome look. Besides backgrounds i never knew to change anything else. 
Yesterday just learnt to change login page. I think that is called GDM themes?
I see on gnome-look.org also metacity, splashscreen and gtk1 and 2. I don't know what all these refer to

don't meanto hijack the thread. I hoped it'd be ok to ask here as i'm trying to learn more 

--
sophtpaw[/QUOTE]

It's the graphical engine that gnome uses. The earlier version was gtk1. KDE uses qt.
So if you want to compile your stuff and you want it to match your desktop it's a good idea to install it the -dev package of it. Many applications today for linux uses gtk2.

---

### Post by Perfect Storm on 2006-05-08
Can you post whole your ./configure for me, it might tell what you are missing.

> checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing

Try install autoconf and automake1.4


Edit: by the way I've checked multiverse for dapper and snes9express is availble there. Perhaps you should check breezy multiverse and see if it's there.

---

### Post by sophtpaw on 2006-05-08
[QUOTE=Artificial Intelligence]It's the graphical engine that gnome uses. The earlier version was gtk1. KDE uses qt.
So if you want to compile your stuff and you want it to match your desktop it's a good idea to install it the -dev package of it. Many applications today for linux uses gtk2.[/QUOTE]

Thank for that AI,

I checked in Synaptic and i have gtk+2x installed(of course aguess) In fact there were many many 'styles'? So, are they like themes for the way the Gui looks? this i'm not quite clear on yet? What would be the difference from simply configuring tabs and icons and backgrounds and wallpapers say. Is it something more fundamental?

thx, 

By the way I love polar bears too and had one for an Avatar a while ago :-({|= 

--
sophtpaw

---

### Post by n11 on 2006-05-08
Oh I am such an idiot. It is there in the multiverse. Sorry for the trouble. Just so you know i installed autoconf and automake-1.4 and did "./configure" again but still didn't work. The same error. Thanks anyways.

---

### Post by hw-tph on 2006-05-08
Follow the wiki page on [how to add more repositories](https://wiki.ubuntu.com/AddingRepositoriesHowto). Make sure you have both the universe and multiverse repositories. Then you can simpy **sudo apt-get install snes9express** to install it.

*Edit: Ahh, you already found it. I'm too slow for my own good.*

---

### Post by Perfect Storm on 2006-05-08
[QUOTE=sophtpaw]Thank for that AI,

I checked in Synaptic and i have gtk+2x installed(of course aguess) In fact there were many many 'styles'? So, are they like themes for the way the Gui looks? this i'm not quite clear on yet? What would be the difference from simply configuring tabs and icons and backgrounds and wallpapers say. Is it something more fundamental?

thx, 

By the way I love polar bears too and had one for an Avatar a while ago :-({|= 

--
sophtpaw[/QUOTE]

It's engines with diffrent options features etc. but I'm no expert on the subjects so I can't tell you specific what the all do.
So if you gonna make a theme you have to decide which engine it should use. Just look at gnome-look.org on the diffrent gtk2+ themes, some says clearlooks other says cairo etc. etc.

---

