---
title: "Trouble compiling and installing libipoddevice-0.5.1"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by saxsux on 2006-10-26
Hi :-)

I'm quite new to ubuntu (I've just installed it on my laptop) and I'm trying to install libipoddevice so I can also install ipod-sharp and use my iPod with Banshee.

The problem is, I can't compile/install it properly. 

Initially, when I ran ./configure, I got errors about there not being a C Compiler. I've run 
```
sudo apt-get install build-essential
```
and that seems to fix it.

But, no when I run it, the output ends with 
```

checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking pkg-config is at least version 0.9.0... yes
checking for LID... configure: error: Package requirements (gobject-2.0        glib-2.0 >= 2.6.0        dbus-1  dbus-glib-1     hal >= 0.5.2    libgtop-2.0 >= 2.12.0   libxml-2.0) were not met:

No package 'gobject-2.0' found
No package 'glib-2.0' found
No package 'dbus-1' found
No package 'dbus-glib-1' found
No package 'hal' found
No package 'libgtop-2.0' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LID_CFLAGS
and LID_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

If I type "make", as per the installation instructions that came with the thing, I get the message "make: *** No targets specified and no makefile found. Stop.".

Typing "make install" results in "make: *** No rule to make target `install'. Stop."


Any help would really be appreciated - I really want to get my iPod working soon!

Thank you :D

---

### Post by RoyArne on 2006-10-26
It seems that you are missing a lot of libraries needed to compile libipod. If you really have to compile libipod yourself you will have to install all of the reported missing packages (and "-dev" packages for them too). But are you absolutely certain that you need to compile these programs yourself? I searched the ubuntu repositories for "ipod" and got the following:

```

rag@wintermute:~$ aptitude search ipod
p   ipod                                         - tool for retrieving informations from iPods
p   ipodder                                      - a podcast receiver
p   ipodslave                                    - kio-slave for ipods
p   ipodslave-dev                                - devlopment files for ipodslave kio-slave
p   libipod-cil                                  - CLI library for accessing iPods
p   libipoddevice-dev                            - library for retrieving informations from iPods
p   libipoddevice0                               - library for retrieving informations from iPods
p   libipodui-cil                                - CLI library for accessing iPods (GUI helpers)
p   libmac-ipod-gnupod-perl                      - access your ipod using perl
p   monodoc-ipod-manual                          - compiled XML documentation for ipod-sharp

```

Also, 

```
rag@wintermute:~$ aptitude show libipod-cil
Package: libipod-cil
State: not installed
Version: 0.5.16-0ubuntu2
Priority: optional
Section: universe/libs
Maintainer: Debian Mono Group <pkg-mono-group@lists.alioth.debian.org>
Uncompressed Size: 139k
Depends: libglib2.0-cil (>= 2.7.90), libipoddevice0 (>= 0.4.5), mono-classlib-1.0 (>= 1.0)
Description: CLI library for accessing iPods
 ipod-sharp is a library that allows manipulation of the iTunesDB used in Apple iPod devices. Currently
 it supports adding/removing songs and manipulating playlists.

```

Can't you just install some of these packages to make your iPod work with banshee? (I use rhythmbox myself).

---

### Post by saxsux on 2006-10-26
Oh! They're in the repositories!

Okay, thanks for the help. Sorry if I was wasting your time :-)

---

### Post by pay on 2006-10-26
You shouldn't be sorry for asking questions on these forums. We're here to help:)

---

