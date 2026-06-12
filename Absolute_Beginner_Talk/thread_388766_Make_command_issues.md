---
title: "Make command issues"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Dhalimu on 2007-03-19
I am extremely new to linux/ubuntu,but I am picking it up pretty well so far. However, I have encountered an error consistently when trying to compile packages/programs from source. I untar the packages, cd into them and run a ./configure on them as per instructions in the packages and online. Every time however, I attempt to run the commands: make, make install, make check; I get the following error.
> make: *** No targets specified and no makefile found.  Stop.


This has happened in each and every package, I have tried to compile the gaim beta and the affinity search program. If anyone could help me I would be greatly indebted.

P.S.:I am running ubuntu under xp in vmware at the moment because I am not the only user of this computer, but from what I have read, this should not cause anything like this. Also, I have tried using a -f and -file an --file flag and specifying the makefile (there are always two, a .am and .in, is this normal?) but this did not work either.

---

### Post by tonyr1988 on 2007-03-19
What does it say at the end of the ./configure command? If it has any errors, it won't produce a makefile, so you won't be able to install it.

Also, I strongly recommend installing checkinstall:

> sudo apt-get install checkinstall

Run that instead of "make install", ie do:

> ./configure
make
sudo checkinstall

If you use "make install", you will have to have the source code to uninstall it. If you use checkinstall, it will put the program as a listing in your Synaptic, so you can manage / remove it from there. I haven't met a single person that doesn't recommend it. :D

---

### Post by Dhalimu on 2007-03-19
Well, my problem somehow dissapeared, after installing checkinstall I tried gaim again, and it worked. No errors on the ./configure, and the make worked perfectly. (going right now) I know now to check for errors on the ./configure though, thank you and the people on irc. (Who explained dependecies to me.)

So the makefile that needs to be generated is the one that has no file extension, not the makefile.am and .in?

---

### Post by njpatel on 2007-03-21
> **Dhalimu said:**
> Well, my problem somehow dissapeared, after installing checkinstall I tried gaim again, and it worked. No errors on the ./configure, and the make worked perfectly. (going right now) I know now to check for errors on the ./configure though, thank you and the people on irc. (Who explained dependecies to me.)

So the makefile that needs to be generated is the one that has no file extension, not the makefile.am and .in?

Hi there,

You sometimes need to do

./autogen.sh

instead of ./configure. If there is an autogeh.sh, use that above ./comfigure. You can pass the same arguments, such as --prefix=/usr/local.

For affinity, you need to run ./autogen.sh, then make, then sudo make install.

-Neil

---

### Post by ElTimo on 2007-03-28
I am having a similar problem, except autogen.sh works fine for me, but make gives me this:

```
Making install in src
make[1]: Entering directory `/home/tim/affinity-search/src'
gcc -pthread -DORBIT2=1 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/libgnome-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/gnome-desktop-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/startup-notification-1.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/freetype2 -I/usr/include/libxml2   -g -Wall -D_GNU_SOURCE -DGNOMELOCALEDIR=\""/usr/local/share/locale"\" -DACTIONDIR=\""/usr/local/share/affinity/actions"\" -DDATADIR=\""/usr/local/share"\"  -I/usr/include/libbeagle -I/usr/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include         -g -O2   -o affinity-applet    
gcc: no input files
make[1]: *** [affinity-applet] Error 1
make[1]: Leaving directory `/home/tim/affinity-search/src'
make: *** [install-recursive] Error 1

```

Any ideas? I'm stumped/too lazy to figure this out. I've tried everything I can think of (granted, not much) and nothing seems to work. Any help would be much appreciated.

---

