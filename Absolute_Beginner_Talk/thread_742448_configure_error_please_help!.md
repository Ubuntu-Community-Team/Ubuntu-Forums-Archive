---
title: "configure: error: please help!"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by animalprimate on 2008-04-01
i want to play crossfire, but when i try to configure it says:

configure: error: You must have the png library installed to compile the client

however ive gotten libpng-1.2.25 from sourceforge and configured it without
any error, still im getting this "configure: error": message when i try to configure
crossfire, *please talk with me and help this problem.*

---

### Post by forrestcupp on 2008-04-01
In a terminal, type
```
sudo apt-get install libpng12-0 libpng12-dev
```
It's probably the dev file it's looking for.

Edit:
I forgot I'm using Hardy now, so I don't know what version Gutsy has.  Open Synaptic and search for libpng and install the appropriate runtime *and* dev package.

---

### Post by smartboyathome on 2008-04-01
You need to install libpng12-dev from synaptic to get it to compile. When it says it is missing x, you usually want to install the dev files.

---

### Post by animalprimate on 2008-04-01
installed that, got further this is the message i get now:

configure: error: curl/curl.h header not found, but metaserver2 support is enable.  Install header file or use --disable-metaserver2

---

### Post by Bachstelze on 2008-04-01
Install *libcurl4-openssl-dev*.

---

### Post by animalprimate on 2008-04-01
i installed that libcurl4... tried configure crossfire again.
heres what is says at the end now:

config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating gtk/Makefile
config.status: WARNING:  gtk/Makefile.in seems to ignore the --datarootdir setting
config.status: creating x11/Makefile
config.status: WARNING:  x11/Makefile.in seems to ignore the --datarootdir setting
config.status: creating common/Makefile
config.status: WARNING:  common/Makefile.in seems to ignore the --datarootdir setting
config.status: creating sound-src/Makefile
config.status: WARNING:  sound-src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating gtk-v2/Makefile
config.status: WARNING:  gtk-v2/Makefile.in seems to ignore the --datarootdir setting
config.status: creating pixmaps/Makefile
config.status: WARNING:  pixmaps/Makefile.in seems to ignore the --datarootdir setting
config.status: creating gtk-v2/src/Makefile
config.status: WARNING:  gtk-v2/src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating help/Makefile
config.status: WARNING:  help/Makefile.in seems to ignore the --datarootdir setting
config.status: creating utils/Makefile
config.status: WARNING:  utils/Makefile.in seems to ignore the --datarootdir setting
config.status: creating common/config.h
config.status: executing depfiles commands
configure:
configure: Configuration summary....
configure:
configure:   Paths
configure:     prefix default value                 /usr/local
configure:     exec_prefix default value            ${prefix}
configure:     Will put executables in              ${exec_prefix}/bin
configure:     Will put config in                   ${prefix}/etc
configure:
configure:   Build options
configure:     Will build GTK1 client?              no
configure:     Will build GTK2 client?              no
configure:     Will build OpenGL renderer?          no
configure:     Will build SDL renderer?             no
configure:     Will build sound server?             yes  (OSS)

im not sure its installed now, i didnt see a way to open it, thanks your avatar is real pretty.

---

### Post by Unix_Slayer on 2008-05-30
I'm getting the same error compiling GCC. Anyone have a clue what's up with Makefile.in?



> **animalprimate said:**
> i installed that libcurl4... tried configure crossfire again.
heres what is says at the end now:

config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating gtk/Makefile
config.status: WARNING:  gtk/Makefile.in seems to ignore the --datarootdir setting
config.status: creating x11/Makefile
config.status: WARNING:  x11/Makefile.in seems to ignore the --datarootdir setting
config.status: creating common/Makefile
config.status: WARNING:  common/Makefile.in seems to ignore the --datarootdir setting
config.status: creating sound-src/Makefile
config.status: WARNING:  sound-src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating gtk-v2/Makefile
config.status: WARNING:  gtk-v2/Makefile.in seems to ignore the --datarootdir setting
config.status: creating pixmaps/Makefile
config.status: WARNING:  pixmaps/Makefile.in seems to ignore the --datarootdir setting
config.status: creating gtk-v2/src/Makefile
config.status: WARNING:  gtk-v2/src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating help/Makefile
config.status: WARNING:  help/Makefile.in seems to ignore the --datarootdir setting
config.status: creating utils/Makefile
config.status: WARNING:  utils/Makefile.in seems to ignore the --datarootdir setting


---

