---
title: "Compiling Issues"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by rustysail on 2007-10-24
Hey I just updated to gutsy, and now I can't compile anything.  I installed build essentials.  I get make errors for everything though.

Any suggestions?

---

### Post by jfinkels on 2007-10-25
Show us what you are trying to compile and the errors you get when trying to compile them!

Have you looked to see if the programs you want are in the repositories?

---

### Post by rustysail on 2007-10-25
Among others.  I was trying to install wmalbum, a dockapp for blackbox.

When I run the configure file I get this.
```

checking for gtk-config... no
checking for GTK - version >= 1.2.10... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Cannot find GTK: Is gtk-config in path?

```

On a different program.  One without a configure file.  wmckgmail-1.1
I ran make
```

root@tux:/home/rusty/.blackbox/dockaps/wmckgmail-1.1# make
cd wmckgmail && make
make[1]: Entering directory `/home/rusty/.blackbox/dockaps/wmckgmail-1.1/wmckgmail'
cc -I/usr/X11R6/share/include -O2 -Den_US.UTF-8 -c -Wall wmckgmail.c -o wmckgmail.o
<command line>:1:6: warning: missing whitespace after the macro name
cc -I/usr/X11R6/share/include -O2 -Den_US.UTF-8 -c -Wall ../wmgeneral/wmgeneral.c -o ../wmgeneral/wmgeneral.o
<command line>:1:6: warning: missing whitespace after the macro name
cc -I/usr/X11R6/share/include -O2 -Den_US.UTF-8 -c -Wall ../wmgeneral/misc.c -o ../wmgeneral/misc.o
<command line>:1:6: warning: missing whitespace after the macro name
cc -I/usr/X11R6/share/include -O2 -Den_US.UTF-8 -c -Wall ../wmgeneral/list.c -o ../wmgeneral/list.o
<command line>:1:6: warning: missing whitespace after the macro name
cc -O2 -Den_US.UTF-8 -o wmckgmail wmckgmail.o ../wmgeneral/wmgeneral.o ../wmgeneral/misc.o ../wmgeneral/list.o -lXext -L/usr/X11R6/lib -lXpm -lXext -lX11 -lm
make[1]: Leaving directory `/home/rusty/.blackbox/dockaps/wmckgmail-1.1/wmckgmail'

```

---

### Post by taurus on 2007-10-25
Looks to me like you need the libgtk-dev package.  Search for it with synaptic and install it.  Then, run your ./configure again.

---

### Post by rustysail on 2007-10-25
Thanks a lot.
But now it is saying that it cannot find gdk-pixbuf

```
checking for GTK - version >= 1.2.10... yes
checking for gdk-pixbuf-config... no
checking for GDK_PIXBUF - version >= 0.15.0... no
*** The gdk-pixbuf-config script installed by GDK_PIXBUF could not be found
*** If GDK_PIXBUF was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GDK_PIXBUF_CONFIG environment variable to the
*** full path to gdk-pixbuf-config.
configure: error: Cannot find gdk-pixbuf

```

I searched for it in the package manager and installed something starting with gdk but no luck.

---

### Post by taurus on 2007-10-25
Look for libgdk-pixbuf2 &  libgdk-pixbuf-dev.

---

### Post by dfreer on 2007-10-25
Basically, when compiling, it'll go something like this:
./configure
Error! missing XYZ!
sudo apt-get install libxyz-dev 
./configure
Error! missing FOOBAR
sudo apt-get install libfoobar-dev

and so on. Try using a site like [http://packages.ubuntu.com/](http://packages.ubuntu.com/) if you need help figuring out which package owns the file that ./configure complains about missing, and things will go much smoother.

---

### Post by rustysail on 2007-10-25
Oh that makes sense.  I was searching for packages with the exact name of the error.  now that I know to put the libxyz-dev in I shouldn't have any more issues.  Thanks a lot.

---

### Post by dfreer on 2007-10-25
That's not always the case, but it is for the most part. Sometimes it will require both the lib, and the lib -dev. The link I mentioned is really helpful IMO, more so than searching thru synaptic or apt-cache.

---

