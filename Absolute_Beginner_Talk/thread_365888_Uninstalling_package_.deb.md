---
title: "Uninstalling package .deb"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by black_ice on 2007-02-20
hello all 

i installed amsn packages.deb and i wan to uninstall it ? 

i'v tried to use dpkg -r amsn and it doesnot work however iam sure that amsn is installed and working 

[PHP] adam@adam-laptop:~$ which amsn
/usr/bin/amsn[/PHP]

[PHP] adam@adam-laptop:~$ sudo dpkg -r amsn
Password:
dpkg - warning: ignoring request to remove amsn which isn't installed.[/PHP]  !!!!!!!!!!!!!!11

---

### Post by Maestro23 on 2007-02-20
Did you get it from the Amsn site?  If so, did you d/l the .run file(pkg) or the .tar file(source)?

Or, did you get it from the Ubuntu repositories via Synaptic or apt-get?

---

### Post by atihimself on 2007-02-20
sudo apt-get remove amsn
i might be wrong, but should work on everything

---

### Post by Jussi Kukkonen on 2007-02-20
dpkg says there's no package called amsn, so if the package is installed it's called something else... Check the .deb file to see what the name of the package is or search for any mentions of "msn" in in stalled packages: ***dpkg-query -l | grep msn***

---

### Post by black_ice on 2007-02-20
no i get it from softpedia and i get it with tar.gz packages and it cannot seen by synaptics 

i run 

[PHP] adam@adam-laptop:~$ dpkg-query -l | grep msn
adam@adam-laptop:~$ 
[/PHP]

nothing happend ?? !!!

---

### Post by JamieC on 2007-02-20
What's the output of these:
```

dpkg-query -l | grep -i msn 

```

```

sudo updatedb
locate -i msn | grep deb

```

Oh wait, I just saw your post, you compiled it from source, right? Do you still have the source files? If so you can do the following (where <path> is the path to the directory containing the source files):
```

cd <path>
sudo make uninstall

```

---

### Post by black_ice on 2007-02-20
here is the output

[PHP] adam@adam-laptop:~$ dpkg-query -l | grep -i msn
ii  kmess                                      1.4.3-2ubuntu1                       Instant messenger to use MSN on KDE
[/PHP]
the second 

[PHP] adam@adam-laptop:~$ locate -i msn | grep deb
/var/cache/apt/archives/amsn_0.95-2.1_i386.deb
/home/adam/.Trash/amsn_0.95-2.1_i386.deb
/home/adam/Sources/Net/amsn/amsn-0.96/utils/webcamsn/src/deblock.c
/home/adam/Sources/Net/amsn/amsn-0.96/utils/webcamsn/src/deblock.o
/home/adam/Sources/Net/amsn/amsn-0.96/debian
/home/adam/Sources/Net/amsn/amsn-0.96/debian/control
/home/adam/Sources/Net/amsn/amsn-0.96/debian/compat
/home/adam/Sources/Net/amsn/amsn-0.96/debian/copyright
/home/adam/Sources/Net/amsn/amsn-0.96/debian/changelog.in
/home/adam/Sources/Net/amsn/amsn-0.96/debian/dirs
/home/adam/Sources/Net/amsn/amsn-0.96/debian/package.postrm
/home/adam/Sources/Net/amsn/amsn-0.96/debian/package.postinst
/home/adam/Sources/Net/amsn/amsn-0.96/debian/rules
/home/adam/Sources/Net/amsn/amsn-0.96/debug.tcl
/home/adam/Sources/Net/amsn/amsn-0.96/amsn.debianmenu
/usr/share/amsn/debug.tcl
[/PHP]

---

### Post by Maestro23 on 2007-02-20
> **black_ice said:**
> here is the output

[PHP] adam@adam-laptop:~$ dpkg-query -l | grep -i msn
ii  kmess                                      1.4.3-2ubuntu1                       Instant messenger to use MSN on KDE
[/PHP]
the second 

[PHP] adam@adam-laptop:~$ locate -i msn | grep deb
/var/cache/apt/archives/amsn_0.95-2.1_i386.deb
/home/adam/.Trash/amsn_0.95-2.1_i386.deb
/home/adam/Sources/Net/amsn/amsn-0.96/utils/webcamsn/src/deblock.c
/home/adam/Sources/Net/amsn/amsn-0.96/utils/webcamsn/src/deblock.o
/home/adam/Sources/Net/amsn/amsn-0.96/debian
/home/adam/Sources/Net/amsn/amsn-0.96/debian/control
/home/adam/Sources/Net/amsn/amsn-0.96/debian/compat
/home/adam/Sources/Net/amsn/amsn-0.96/debian/copyright
/home/adam/Sources/Net/amsn/amsn-0.96/debian/changelog.in
/home/adam/Sources/Net/amsn/amsn-0.96/debian/dirs
/home/adam/Sources/Net/amsn/amsn-0.96/debian/package.postrm
/home/adam/Sources/Net/amsn/amsn-0.96/debian/package.postinst
/home/adam/Sources/Net/amsn/amsn-0.96/debian/rules
/home/adam/Sources/Net/amsn/amsn-0.96/debug.tcl
/home/adam/Sources/Net/amsn/amsn-0.96/amsn.debianmenu
/usr/share/amsn/debug.tcl
[/PHP]

Try what JamieC posted for source.  It is very important to know how you installed something for when the time comes to uninstall it.  That is why I asked how you installed it. You installed from source, so neither Synaptic or dpkg will have any bearing on this.  Same thing win installing with apt-get and aptitude.

---

### Post by mcduck on 2007-02-20
If you really installed it from a .deb package (like you said in your first post) then it _is_ listed in Synaptic. Just use the search to find it..

Everything installed from .deb packages shows in Synaptic, no matter how you install it (apt-get, aptitude, gnome-app-install, Synaptic and all other Ubuntu's package management tools use .deb packages).

---

### Post by black_ice on 2007-02-20
i tried what he have said 

[PHP] adam@adam-laptop:/usr/share/amsn$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
[/PHP]

---

### Post by Maestro23 on 2007-02-20
> **mcduck said:**
> If you really installed it from a .deb package (like you said in your first post) then it _is_ listed in Synaptic. Just use the search to find it..

In his other post, he said it was a .tar.gz file.

BlackIce, can you get back to the directory that was created when you extracted the file(Source Directory).  Get there and run the "make uninstall" command again.

If that doesn't work, is there a README file in there somewhere.

---

### Post by black_ice on 2007-02-20
So ... 

what u think about what i need to remove this package i need to uninstall it .......

by the way thanx for all

---

### Post by Jussi Kukkonen on 2007-02-20
> **black_ice said:**
> i tried what he have said 

[PHP] adam@adam-laptop:/usr/share/amsn$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
[/PHP]
black_ice, you should be in the *source* directory like JAmieC said. The same directory you were in when you installed it. Probably /home/adam/Sources/Net/amsn/ or some subdir of that...

---

### Post by black_ice on 2007-02-20
thanx for care i tried what u said
and here is the output 

[PHP] root@adam-laptop:/home/adam/Sources/Net/amsn/amsn-0.96# ./configure
checking for prefix by checking for wish... /usr/bin/wish
checking for gcc... gcc
checking for C compiler default output file name... a.out
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
checking tcl build dir... using tcl library in /usr/lib/tcl8.4
checking tk build dir... using tk library in /usr/lib/tk8.4
checking for main in -lstdc++... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for egrep... grep -E
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
checking for png_read_info in -lpng... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking for jpeg_CreateDecompress in -ljpeg... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking jerror.h usability... yes
checking jerror.h presence... yes
checking for jerror.h... yes
checking for ftello... yes
checking for fseeko... yes
checking for getpt... yes
checking for strcasestr... yes
checking for memmem... yes
checking for dlopen... no
checking for pthread_create in -lpthread... yes
checking if mmx should be used... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating utils/linux/capture/config.h
config.status: utils/linux/capture/config.h is unchanged

compile time options summary
============================

    X11          : yes
    Tcl          : 8.4
    TK           : 8.4
    DEBUG        : no
    STATIC       : no

root@adam-laptop:/home/adam/Sources/Net/amsn/amsn-0.96# make 
make: Nothing to be done for `build'.
root@adam-laptop:/home/adam/Sources/Net/amsn/amsn-0.96# make unistall
make: *** No rule to make target `unistall'.  Stop.
[/PHP]

---

### Post by Jussi Kukkonen on 2007-02-20
> # make unistall 
missing an 'n' there.

---

