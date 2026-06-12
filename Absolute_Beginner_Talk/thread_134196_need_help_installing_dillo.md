---
title: "need help installing dillo"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-02-21
ok, i'm stuck. i'm trying to install dillo, with some alterations (different toolbar icons and enabling SSL, whatever that is). i got it untarred, i made my changes, i'm in the directory and ready for installation. i did *./configure --help* and decided i would just do *./configure* and see what happens. i got this...

[i]checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH[/i]

i have gcc-3.3 and 4 base installed. please keep in mind that i don't know what i'm doing so feel free to insult my intelligence with the obvious. thanks.

---

### Post by fuscia on 2006-02-21
it appears i've gotten past that one. now, i'm getting this, after running ./configure...

[i]checking for glib-config... no
checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: Unable to find glib with a version >= 1.2.0. Dillo NEEDS glib[/i]

---

### Post by kaamos on 2006-02-21
```
alaisi@ubuntu:~$ apt-cache search libglib | grep dev
libglib1.2-dev - Development files for GLib library
libglib2.0-dev - Development files for the GLib library
libglibmm-2.4-dev - C++ wrapper for the GLib toolkit (development files)

```
So
```
sudo apt-get install libglib1.2-dev libglib2.0-dev
```

---

### Post by AgenT on 2006-02-21
Make sure you have this package installed before you compile any program:
```
build-essential
``` For further help, consult the README and INSTALL file that came with the source code. These will tell you the requirements to compile. Notice that if the requirement is libX that means you should install both libX and libX-dev. libX is used when running the program and libX-dev is used when you compile the program. You should install both.

---

### Post by fuscia on 2006-02-21
ok, 'build-essential' was the answer to the first post. i got that. thanks, agenT. i got the glib1.2 thing. thanks, kaamos. now, i'm getting an error because i don't have GTK+1.2. it's not in synaptic. should i do the apt-get thing?

dillo is in synaptic and i had been using that version when i decided i wanted to make some changes. maybe this is a dumb as hell question, but how was i able to use that version, but not be able to configure this version? (the README said dillo would not compile on 2.0.)

---

### Post by kaamos on 2006-02-21
It's probably "libgtk1.2-dev". Just search gtk in synaptic and try to spot packages with -dev. Apt shows the same packages as synaptic.

---

### Post by fuscia on 2006-02-21
LOL! it looks like i finally got everything i need installed. i ran *make* and got pages of error and warning messages. as kenny rogers once sang "you gotta know when to hold 'em. know when to fold 'em." so, in the words of the immortal jackie gleason "GOOD NIGHT, EVERYBODY!!!"

kaamos and agenT, i appreciate your efforts to help me. this was a good learning experience. i'm not giving up. i'm just going to try this on something a little less ambitious. thanks.

---

### Post by fuscia on 2006-02-22
whoop-dee-doo, i finally did it (thanks to all the help i got). the one thing that i have trouble with this linux stuff is, you just can't wing it as much. oh well, i guess i'll have to learn to be more diligent. thanks again for the help.

---

