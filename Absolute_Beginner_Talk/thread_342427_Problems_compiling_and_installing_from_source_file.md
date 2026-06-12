---
title: "Problems compiling and installing from source files"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Josh_b on 2007-01-20
Hey,

This is my first go of compiling from source file and it hasn't gone well. I tried to install a game, GTKLife, off of a "Linux Format" (Magazine) disc. I follow the instructions and unpack the tar file with;
```
tar xzvf /media/cdrom0/Hot_Picks/GtkLife/gtklife-5.1.tar.gz
```
I then go to that directory and use;
```
./configure
```
and it gives me an error about GTK+
So I looked around on the cd and found GTK+ with necessary dependencies. I try installing GTK+ and the dependencies in a multitude of different orders (after finding out I didn't have build-essential installed), but to no avail. Then I got reconnected to the net so searched synaptic for the required packages. I installed libgtk2.0 with all dependencies suggested. Now when I run the ./configure it gives me this:
> checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
Gtk 1.2 not found, trying Gtk 2...
checking for pkg-config... /usr/local/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: Gtk+ is required

I also installed pkg-config.

Can someone please help me. I have no idea how to get this to work. :(

Josh

---

### Post by po0f on 2007-01-20
Josh_b,

From a terminal:
```
[FONT="Courier New"]$ sudo aptitude update
$ sudo aptitude install libgtk2.0-dev libgtk1.2-dev[/FONT]
```

---

### Post by Josh_b on 2007-01-20
That worked. Thanks a bunch. :)

Josh

---

