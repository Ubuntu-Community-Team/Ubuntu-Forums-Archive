---
title: "Error Installing Audacious"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by urk_nono on 2007-04-01
I downloaded the audacious .1.3.1 from [http://audacious-media-player.org/Downloads](http://audacious-media-player.org/Downloads) and extracted the file to my Desktop. When I wanted to install it, this occured:

**$ ./configure**
[I]checking for what extension and flags to use for plugin compilation... libdl-compatible: -fPIC -DPIC -shared, .so
checking if you are running Apple-GCC... no
checking for libmcs >= 0.1... no
configure: error: Cannot find libmcs[/I]

**$ make**
[I]Makefile:3: ../mk/rules.mk: No such file or directory
make[1]: *** No rule to make target `../mk/rules.mk'.  Stop.
make: *** [depend] Error 2
[/I]

**$ sudo make install**
[I]Makefile:3: ../mk/rules.mk: No such file or directory
make[1]: *** No rule to make target `../mk/rules.mk'.  Stop.
make: *** [depend] Error 2[/I]

Does anyone know what to do?

Kind Regards, Urk

---

### Post by 3rdalbum on 2007-04-01
There are two things you can do:

1. Wait for Ubuntu 7.04 to be released, upgrade to that, and install Audacious through the repositories.

2. OR download and install all the packages from this page: [http://mail.atheme.org/~soho/](http://mail.atheme.org/~soho/)

You downloaded the source code; it's not really recommended for new users to download source code because it's a bit trickier to install. The link I just gave you is for .deb packages, designed for Ubuntu. Try to find a .deb whenever you can.

---

### Post by urk_nono on 2007-04-01
Thanks! I'm starting to get the hang of basic comprehension of Ubuntu. I'll get to it once I get home from work.

---

### Post by Perfect Storm on 2007-04-01
Audacious have a repo you can add, but it's not v1.3.x but 1.2.x

---

### Post by conceited on 2007-04-01
thank you very much, i was having troubles also with the source.

it was saying that i didn't have some libs installed, which were.

but the 2nd option you gave worked perfectly..
don't forget people, you need to install the plugins, they have the codecs for mp3's a nd what not in them :)

---

