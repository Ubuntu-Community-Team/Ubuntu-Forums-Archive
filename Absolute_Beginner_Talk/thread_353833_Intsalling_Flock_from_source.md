---
title: "Intsalling Flock from source"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-05
i am following ubuntuguide.org, have downloaded code for flock 0.7.10
have extracted it, this is what happens:


shoaibi@saber-rider:~/flock$ ./configure
bash: ./configure: No such file or directory
shoaibi@saber-rider:~/flock$ make
make: *** No targets specified and no makefile found.  Stop.
shoaibi@saber-rider:~/flock$ sudo make install
make: *** No rule to make target `install'.  Stop.



any idea what should i do?
i wanna make its deb file once and for all to use that install of installing from source again and again.

PS: i have installed Build-Essential Compilers

---

### Post by shoaibi on 2007-02-05
whereas the flock directory exists and all files are there....

---

### Post by shoaibi on 2007-02-05
hmmm seems nobody inteterested to help or either evryone is too busy today :( :'(

---

### Post by lamego on 2007-02-05
[quote]shoaibi@saber-rider:~/flock$ ./configure[quote]
Make sure that is the directory were you have extracted the files into. It was not.

Please note that the .tar.gz on the main download page is a binary package, it's not the source...

---

### Post by shoaibi on 2007-02-05
its the directory, i have verified, hmmmso now what to do? how to install?

---

### Post by renzokuken on 2007-02-05
could you list the contents of the flock directory

---

### Post by shoaibi on 2007-02-05
shoaibi@saber-rider:~$ cd flock
shoaibi@saber-rider:~/flock$ ls
browserconfig.properties
libnspr4.so
libxpcom.so
chrome
libnss3.so
libxpistub.so
components
libnssckbi.so
mozilla-xremote-client
defaults
libplc4.so
plugins
extensions
libplds4.so
res
flock
libsmime3.so
run-mozilla.sh
flock-bin
libsoftokn3.chk
searchplugins
gm
libsoftokn3.so
updater
greprefs
libssl3.so
updater.ini
icons
libxpcom_compat.so
xpicleanup
libmozjs.so
libxpcom_core.so

---

### Post by renzokuken on 2007-02-05
ok, the ./configure, make, make install steps are for compiling something from source. flock doesnt need compiling since it is pre-compiled by the looks of things. all you need to do is cd to the directory and type flock

EDIT:

have look here [http://brentroos.com/2006/07/24/install-flock-on-ubuntu/](http://brentroos.com/2006/07/24/install-flock-on-ubuntu/)

---

