---
title: "Kiba-dock help (solved)"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2006-10-29
EDIT!!!
I still can not get kiba-dock to work.( :( )
Most of the problems can be found below in this thread.

!!! I have tried the .deb files and it says "Error: Dependency is not satisfiable: libatk1.0-0" !!!
I have this installed what should I change to get this to work

---

### Post by taurus on 2006-10-29
There shouldn't be a space between n and .!!!

```
sudo ./autogen.sh
```

---

### Post by spyker3292 on 2006-10-29
> **taurus said:**
> There shouldn't be a space between n and .!!!

```
sudo ./autogen.sh
```

No help
> $ sudo ./autogen.sh
Password:
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
aclocal:configure.in:37: warning: macro `AM_GCONF_SOURCE_2' not found in libraryautoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.in: installing `./install-sh'
configure.in: installing `./missing'
akamaru/Makefile.am: installing `./depcomp'
Makefile.am: installing `./INSTALL'
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

---

### Post by PriceChild on 2006-10-29
```
sudo apt-get install build-essential gcc
```

---

### Post by taurus on 2006-10-29
Looks like you've started a new thread for this...  From a terminal, run

```
sudo aptitude update
sudo aptitude install build-essential
```
Then, run that command again and let me know what happens...

---

### Post by spyker3292 on 2006-10-29
> **taurus said:**
> Looks like you've started a new thread for this...  ya

Still problem
> ~/kiba-dock$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
aclocal:configure.in:37: warning: macro `AM_GCONF_SOURCE_2' not found in libraryautoreconf: configure.in: tracing
autoreconf: configure.in: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.in:37: error: possibly undefined macro: AM_GCONF_SOURCE_2
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1


---

### Post by taurus on 2006-10-29
Is there a INSTALL in that directory and if there is, can you paste it here?

```
more INSTALL
```

---

### Post by PriceChild on 2006-10-29
If i were you, i'd re-extract the tar and start again...

starting again worked for me when i built it :P

---

### Post by distroman on 2006-10-29
[http://forum.beryl-project.org/topic-3841-info-post](http://forum.beryl-project.org/topic-3841-info-post)

You might need to upgrade to automake1.9.6-4, if your using dapper.

---

### Post by spyker3292 on 2006-10-29
> **PriceChild said:**
> If i were you, i'd re-extract the tar and start again...

starting again worked for me when i built it :P

Ok here's what happened... uhh too much to post. LONG!

---

### Post by PriceChild on 2006-10-29
> **distroman said:**
> [http://forum.beryl-project.org/topic-3841-info-post](http://forum.beryl-project.org/topic-3841-info-post)

You might need to upgrade to automake1.9.6-4, if your using dapper.Yeah... check... my sig for a howto with details.

---

### Post by taurus on 2006-10-29
> **spyker3292 said:**
> Ok here's what happened... uhh too much to post. LONG!
Yes, it's a long file.  Just want to see the first two screens of it...  ;)

---

### Post by distroman on 2006-10-29
> **PriceChild said:**
> Yeah... check... my sig for a howto with details.
Nice.

---

### Post by spyker3292 on 2006-10-29
Tried again
after sudo checkinstall I get
> checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>>

What should the description be

---

### Post by PriceChild on 2006-10-29
Yay its working for you :)

Whatever you want.... "kiba-dock by meeee!" for example.

---

### Post by spyker3292 on 2006-10-29
> **PriceChild said:**
> Yay its working for you :)

Whatever you want.... "kiba-dock by meeee!" for example.

And now this happens :( 
(at the bottom FAILED) and it says to you want to see the log tell me if you need it.
```
 sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> My Kiba-Dock
>>

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package version "dock" does not
*** Warning: contain any digits. dpkg might not like that.

This package will be built according to these values:

0 -  Maintainer: [ root@jacks-linux-comp ]
1 -  Summary: [ Package created with checkinstall 1.6.0 ]
2 -  Name:    [ kiba ]
3 -  Version: [ dock ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ kiba-dock ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
Making install in akamaru
make[1]: Entering directory `/home/jack/Desktop/kiba-dock/akamaru'
make[2]: Entering directory `/home/jack/Desktop/kiba-dock/akamaru'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'akamaru' '/usr/bin/akamaru'
/usr/bin/install: setting permissions for `/usr/bin/akamaru': No such file or directory
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/jack/Desktop/kiba-dock/akamaru'
make[1]: Leaving directory `/home/jack/Desktop/kiba-dock/akamaru'
Making install in dock
make[1]: Entering directory `/home/jack/Desktop/kiba-dock/dock'
make[2]: Entering directory `/home/jack/Desktop/kiba-dock/dock'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'kiba-dock' '/usr/bin/kiba-dock'
/usr/bin/install: setting permissions for `/usr/bin/kiba-dock': No such file or directory
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/jack/Desktop/kiba-dock/dock'
make[1]: Leaving directory `/home/jack/Desktop/kiba-dock/dock'
Making install in gset-kiba
make[1]: Entering directory `/home/jack/Desktop/kiba-dock/gset-kiba'
make[2]: Entering directory `/home/jack/Desktop/kiba-dock/gset-kiba'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'gset-kiba' '/usr/bin/gset-kiba'
/usr/bin/install: setting permissions for `/usr/bin/gset-kiba': No such file or directory
test -z "/usr/share/kiba-dock" || mkdir -p -- "/usr/share/kiba-dock"
 /usr/bin/install -c -m 644 'gset-kiba.glade' '/usr/share/kiba-dock/gset-kiba.glade'
/usr/bin/install: setting permissions for `/usr/share/kiba-dock/gset-kiba.glade': No such file or directory
make[2]: Leaving directory `/home/jack/Desktop/kiba-dock/gset-kiba'
make[1]: Leaving directory `/home/jack/Desktop/kiba-dock/gset-kiba'
Making install in icons
make[1]: Entering directory `/home/jack/Desktop/kiba-dock/icons'
make[2]: Entering directory `/home/jack/Desktop/kiba-dock/icons'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/icons/hicolor/128x128/apps" || mkdir -p -- "/usr/share/icons/hicolor/128x128/apps"
 /usr/bin/install -c -m 644 'kiba_128.png' '/usr/share/icons/hicolor/128x128/apps/kiba_128.png'
/usr/bin/install: setting permissions for `/usr/share/icons/hicolor/128x128/apps/kiba_128.png': No such file or directory
test -z "/usr/share/icons/hicolor/16x16/apps" || mkdir -p -- "/usr/share/icons/hicolor/16x16/apps"
 /usr/bin/install -c -m 644 'kiba_16.png' '/usr/share/icons/hicolor/16x16/apps/kiba_16.png'
/usr/bin/install: setting permissions for `/usr/share/icons/hicolor/16x16/apps/kiba_16.png': No such file or directory
test -z "/usr/share/icons/hicolor/24x24/apps" || mkdir -p -- "/usr/share/icons/hicolor/24x24/apps"
 /usr/bin/install -c -m 644 'kiba_24.png' '/usr/share/icons/hicolor/24x24/apps/kiba_24.png'
/usr/bin/install: setting permissions for `/usr/share/icons/hicolor/24x24/apps/kiba_24.png': No such file or directory
test -z "/usr/share/icons/hicolor/48x48/apps" || mkdir -p -- "/usr/share/icons/hicolor/48x48/apps"
 /usr/bin/install -c -m 644 'kiba_48.png' '/usr/share/icons/hicolor/48x48/apps/kiba_48.png'
/usr/bin/install: setting permissions for `/usr/share/icons/hicolor/48x48/apps/kiba_48.png': No such file or directory
test -z "/usr/share/icons/hicolor/64x64/apps" || mkdir -p -- "/usr/share/icons/hicolor/64x64/apps"
 /usr/bin/install -c -m 644 'kiba_64.png' '/usr/share/icons/hicolor/64x64/apps/kiba_64.png'
/usr/bin/install: setting permissions for `/usr/share/icons/hicolor/64x64/apps/kiba_64.png': No such file or directory
make[2]: Leaving directory `/home/jack/Desktop/kiba-dock/icons'
make[1]: Leaving directory `/home/jack/Desktop/kiba-dock/icons'
Making install in utils
make[1]: Entering directory `/home/jack/Desktop/kiba-dock/utils'
make[2]: Entering directory `/home/jack/Desktop/kiba-dock/utils'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
 /usr/bin/install -c 'kiba-icon-editor.py' '/usr/bin/kiba-icon-editor.py'
/usr/bin/install: setting permissions for `/usr/bin/kiba-icon-editor.py': No such file or directory
 /usr/bin/install -c 'kiba-systray.py' '/usr/bin/kiba-systray.py'
/usr/bin/install: setting permissions for `/usr/bin/kiba-systray.py': No such file or directory
 /usr/bin/install -c 'populate-dock.sh' '/usr/bin/populate-dock.sh'
/usr/bin/install: setting permissions for `/usr/bin/populate-dock.sh': No such file or directory
test -z "/usr/share/kiba-dock" || mkdir -p -- "/usr/share/kiba-dock"
 /usr/bin/install -c -m 644 'kiba-icons.glade' '/usr/share/kiba-dock/kiba-icons.glade'
/usr/bin/install: setting permissions for `/usr/share/kiba-dock/kiba-icons.glade': No such file or directory
make[2]: Leaving directory `/home/jack/Desktop/kiba-dock/utils'
make[1]: Leaving directory `/home/jack/Desktop/kiba-dock/utils'
Making install in files
make[1]: Entering directory `/home/jack/Desktop/kiba-dock/files'
make[2]: Entering directory `/home/jack/Desktop/kiba-dock/files'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/python2.4/site-packages" || mkdir -p -- "/usr/lib/python2.4/site-packages"
 /usr/bin/install -c -m 644 'SimpleGladeApp.py' '/usr/lib/python2.4/site-packages/SimpleGladeApp.py'
/usr/bin/install: setting permissions for `/usr/lib/python2.4/site-packages/SimpleGladeApp.py': No such file or directory
test -z "/etc/gconf/schemas" || mkdir -p -- "/etc/gconf/schemas"
 /usr/bin/install -c -m 644 'kiba.schemas' '/etc/gconf/schemas/kiba.schemas'
/usr/bin/install: setting permissions for `/etc/gconf/schemas/kiba.schemas': No such file or directory
make[2]: Leaving directory `/home/jack/Desktop/kiba-dock/files'
make[1]: Leaving directory `/home/jack/Desktop/kiba-dock/files'
make[1]: Entering directory `/home/jack/Desktop/kiba-dock'
make[2]: Entering directory `/home/jack/Desktop/kiba-dock'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/jack/Desktop/kiba-dock'
make[1]: Leaving directory `/home/jack/Desktop/kiba-dock'

======================== Installation successful ==========================

Copying documentation directory...
./
./AUTHORS
./COPYING
./ChangeLog
./INSTALL
./NEWS
./README
./TODO

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

```

---

### Post by spyker3292 on 2006-10-29
Help

---

### Post by spyker3292 on 2006-10-29
bump

---

### Post by spyker3292 on 2006-10-30
Could someone please help I have been trying to do this for a while.](*,) :confused:

---

### Post by spyker3292 on 2006-10-30
EDIT ON FIRST POST!!! (Is ANYONE trying to help now its been quite a while)
(bump)

---

### Post by Vurius on 2006-11-02
Simple.  Add a number to the version, where it says dock.

---

### Post by spyker3292 on 2006-11-02
> **Vurius said:**
> Simple.  Add a number to the version, where it says dock.


WAIT never mind....
when it is open the dock bacground is black how do I make it transparent? and when i put my mouse on the launchers they turn black and dont work....

---

### Post by Hexydes on 2006-12-02
> **Vurius said:**
> Simple.  Add a number to the version, where it says dock.

I'm getting the same error, where it is failing to install the package. I tried changing the version number, but got the same result. Any other ideas as to what could be causing this?

Thanks!

---

### Post by Hexydes on 2006-12-02
Ok, well....no idea what's up. I'm still getting the error when I try to build the package, but for some reason, it is building it. I copied the .deb file to a new location, ran it, and kiba-dock is now installed and running fine. Go figure.

Anyway, I'm attaching the .deb file, so anyone with AMD64 Ubuntu, this should hopefully allow you to install and run kiba-dock. If you have questions....don't ask me. I have no idea. :P

---

### Post by Hexydes on 2006-12-02
Hmm, this was working fine, now when I load kiba-dock up, it loads up fine, but as soon as I mouse over any of the icons, it crashes, and the terminal shows:

```
Floating point exception (core dumped)
```

Any ideas?

---

### Post by Hexydes on 2006-12-03
No ideas on this one? I'm really stumped, and really want to get kiba-dock running again! :)

---

### Post by Hexydes on 2006-12-06
Oh well, so much for kiba-dock...

---

