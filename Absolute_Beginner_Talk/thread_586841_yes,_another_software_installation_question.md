---
title: "yes, another software installation question"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by thespankguy on 2007-10-22
i've read all the tutorials on how to install software but can't seem to figure this out. i downloaded a tar.gz file to my desktop. i right click, click "extract here".  this is what i did in the terminal:

```
steven@steven-desktop:~$ ls
Desktop    gnotify-1.2             index.html  Pictures  Templates
Documents  gtk-gnutella-downloads  Music       Public    Videos
steven@steven-desktop:~$ cd gnotify-1.2
steven@steven-desktop:~/gnotify-1.2$ ./configure
configure: error: cannot find install-sh or install.sh in . ./.. ./../..
steven@steven-desktop:~/gnotify-1.2$ make
make  all-recursive
make[1]: Entering directory `/home/steven/gnotify-1.2'
Making all in include
make[2]: Entering directory `/home/steven/gnotify-1.2/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/steven/gnotify-1.2/include'
Making all in src
make[2]: Entering directory `/home/steven/gnotify-1.2/src'
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DXTHREADS -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libxml2     `pkg-config --cflags libxml-2.0`    -Wall   -O3  -c gnotify.c
Package libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml-2.0' found
In file included from gnotify.c:17:
../include/gnotify.h:22:21: error: gtk/gtk.h: No such file or directory
../include/gnotify.h:40:30: error: libxml/xmlmemory.h: No such file or directory
../include/gnotify.h:41:27: error: libxml/parser.h: No such file or directory
In file included from gnotify.c:17:
../include/gnotify.h:125: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:126: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:127: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:128: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:129: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:130: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:131: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:132: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:133: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:134: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:135: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:144: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:145: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:146: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:174: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:175: error: expected ‘)’ before ‘*’ token
../include/gnotify.h:176: error: expected ‘)’ before ‘*’ token
gnotify.c: In function ‘gnotify_main’:
gnotify.c:175: warning: pointer targets in passing argument 3 of ‘accept’ differ in signedness
make[2]: *** [gnotify.o] Error 1
make[2]: Leaving directory `/home/steven/gnotify-1.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steven/gnotify-1.2'
make: *** [all-recursive-am] Error 2
steven@steven-desktop:~/gnotify-1.2$ 

```

gnotify-1.2 is what i'm trying to install, and it is the title of the folder that extracted to my desktop. as you can see, ./configure doesn't work, so i just tried "make" which gave me what you see there. any help?

---

### Post by SOULRiDER on 2007-10-22
What youre trying to do there is compile a program from source. You need some tools to do that like build-essential and checkinstall. 

What you most likely want to do is intall the application from the repositories. Just fire up Synaptic and look for it. Synaptic will automatically download and install it for you. If you cant find it on synaptic look for a DEB package for Ubuntu which you can download and double click to install.

---

### Post by thespankguy on 2007-10-22
is Synaptic the add/remove programs thing? if so, i already searched for gnotify and couldn't find it. however, when you told me to look there i also simply searched for "gmail" and found exactly what i was looking for. i'm amazed at the simplicity of linux so far; i was making it far too complex. thanks

---

### Post by Steveway on 2007-10-22
You should not use ./configure on that program.
Do a:
sh autogen.sh
if that does not return any errors then do a:
make
and finally a:
sudo make install
if you have checkinstall installed then you should do:
sudo checkinstall
instead of sudo make install
If it spits out any errors it is most propably telling you that you are missing some dependencies, it should say what you need so look into Synaptic for the package.
And keep in mind, for compiling you need the -dev packages.

---

### Post by oldos2er on 2007-10-22
Were you looking for gmail-notify? It's in the repositories; so 'sudo aptitude install gmail-notify' in a terminal should work.

---

### Post by Maestro23 on 2007-10-22
For future reference: 

Installing Software: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

How to Install Anything in Ubuntu: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by thespankguy on 2007-10-22
> **Maestro23 said:**
> For future reference: 

Installing Software: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

How to Install Anything in Ubuntu: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

i read those and thought i was doing everything correctly, which is why i posted.

 i did search in synaptic for "gnotify" and couldn't find it. i DID however find it once i searched for "gmail".

---

