---
title: "gtk+ 2 compile problem (i need to get rid of glib 2.11)"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by silentjudas on 2007-05-29
ok, it tells me i need to get rid of glib 2.11.0, but i dont know how (yes i have 2.12, but it says i HAVE to remove .11)

```

checking for GLIB - version >= 2.12.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.12.12, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.12.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.


```

---

### Post by silentjudas on 2007-05-29
well? anyone?

---

### Post by KIAaze on 2007-05-29
You could try to simply remove it via synaptic package manager. (search for glib and unmark the one you want to remove)

Otherwise you could try to set the LD_LIBRARY_PATH or PKG_CONFIG_PATH environment variables.

Look into ```
man pkg-config
``` for more info.

---

### Post by silentjudas on 2007-05-29
well it aint in synaptic....

and i def. have no clue how to do the other way

---

### Post by silentjudas on 2007-05-30
...help please....

er


sudo help please? 

lol

---

### Post by silentjudas on 2007-05-30
oh come on guys. please help me out here

---

### Post by KIAaze on 2007-05-31
Since I also had some library problems last night, I did some research.
To solve your problem, you should understand what's going on.
I assume that your error appears when running the "./configure" command to install a program from source.

_EXPLANATION:_
So here's an explanation of where I think your error comes from **(quick solutions are at the end ;) )**:

Go into /usr/lib and list the libglib* files there with the "-l" option:
```
>cd /usr/lib
>ls -l libglib*
```

Here's the output on my PC for example:
```
[B]lrwxrwxrwx 1 root root      21 2007-03-05 19:26 libglib-1.2.so.0 -> libglib-1.2.so.0.0.10
-rw-r--r-- 1 root root  154272 2007-03-05 06:14 libglib-1.2.so.0.0.10
-rw-r--r-- 1 root root 1096324 2007-05-24 17:11 libglib-2.0.a
-rw-r--r-- 1 root root     823 2007-05-24 17:10 libglib-2.0.la
_lrwxrwxrwx 1 root root      23 2007-05-25 08:43 libglib-2.0.so -> libglib-2.0.so.0.1300.2_
lrwxrwxrwx 1 root root      23 2007-05-25 08:43 libglib-2.0.so.0 -> libglib-2.0.so.0.1300.2
-rw-r--r-- 1 root root  756524 2007-05-24 17:11 libglib-2.0.so.0.1300.2
-rw-r--r-- 1 root root  222512 2007-03-05 06:14 libglib.a
-rw-r--r-- 1 root root     714 2007-03-05 06:14 libglib.la[/B]
-rw-r--r-- 1 root root  409376 2005-12-11 02:29 libglibmm-2.0.a
-rw-r--r-- 1 root root     949 2005-12-11 02:28 libglibmm-2.0.la
lrwxrwxrwx 1 root root      23 2007-04-14 22:03 libglibmm-2.0.so -> libglibmm-2.0.so.1.5.11
lrwxrwxrwx 1 root root      23 2007-04-14 22:03 libglibmm-2.0.so.1 -> libglibmm-2.0.so.1.5.11
-rw-r--r-- 1 root root  270152 2005-12-11 02:29 libglibmm-2.0.so.1.5.11
-rw-r--r-- 1 root root  464838 2007-05-01 21:38 libglibmm-2.4.a
-rw-r--r-- 1 root root     961 2007-05-01 21:37 libglibmm-2.4.la
lrwxrwxrwx 1 root root      23 2007-05-05 20:41 libglibmm-2.4.so -> libglibmm-2.4.so.1.0.24
lrwxrwxrwx 1 root root      23 2007-05-05 20:41 libglibmm-2.4.so.1 -> libglibmm-2.4.so.1.0.24
-rw-r--r-- 1 root root  330368 2007-05-01 21:38 libglibmm-2.4.so.1.0.24
-rw-r--r-- 1 root root   16280 2007-05-01 21:38 libglibmm_generate_extra_defs-2.4.a
-rw-r--r-- 1 root root    1101 2007-05-01 21:37 libglibmm_generate_extra_defs-2.4.la
lrwxrwxrwx 1 root root      43 2007-05-05 20:41 libglibmm_generate_extra_defs-2.4.so -> libglibmm_generate_extra_defs-2.4.so.1.0.24
lrwxrwxrwx 1 root root      43 2007-05-05 20:41 libglibmm_generate_extra_defs-2.4.so.1 -> libglibmm_generate_extra_defs-2.4.so.1.0.24
-rw-r--r-- 1 root root   13044 2007-05-01 21:38 libglibmm_generate_extra_defs-2.4.so.1.0.24
lrwxrwxrwx 1 root root      21 2007-04-14 21:39 libglib.so -> libglib-1.2.so.0.0.10

```

As you can see, a lot of the libraries are in fact links to other files (links="->").

When you run "./configure", you are in fact preparing the Makefile, which will allow you to compile the program by running "make" later on.
Among other thins you are creating the PACKAGE_LIBS variable which lists the libraries needed by the program.
It can be found in Makefiles and looks like this for example:
```
PACKAGE_LIBS='-lgtkdatabox -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  '
```

This line of -lXXX stuff will be used dueing compilation by a gcc/g++ command.
The used libraries will then be the libXXX.so found in /usr/lib.
In your case: libglib-2.0.so .

But the configure script not only creates the PACKAGE_LIBS, it also checks that the correct version is installed.
The libraries for which it checks can be found easily in the "configure.in" file if it is available.
(Inside the configure script it's more complex. configure.in is a simple file used to generate the configure script.)

Here's what you can find in configure.in:
```
PKG_CHECK_MODULES(PACKAGE, [gtk+-2.0 gdk-2.0 gtkdatabox])
```

Your error message tells you about the pkg-config command:
```
>pkg-config --modversion glib-2.0
2.13.2
```
It's what the configure script uses to get the version of the installed libraries.

Here's the "man" description of pkg-config:

```
 The pkg-config program is used to retrieve information about installed libraries in the system.  It is typically used to compile and
       link against one or more libraries.  Here is a typical usage scenario in a Makefile:

       program: program.c
            cc program.c &#8216;pkg-config --cflags --libs gnomeui&#8216;

       [B]pkg-config retrieves information about packages from special metadata files. These files are  named  after  the  package,  with  the
       extension  _.pc_.  By default, pkg-config looks in the directory _prefix/lib/pkgconfig_ for these files;[/B] it will also look in the colon-
       separated (on Windows, semicolon-separated) list of directories specified by the PKG_CONFIG_PATH environment variable.

       The package name specified on the pkg-config command line is defined to be the name of the metadata file, minus the  .pc  extension.
       If  a  library can install multiple versions simultaneously, it must give each version its own name (for example, GTK 1.2 might have
       the package name "gtk+" while GTK 2.0 has "gtk+-2.0").
```

"prefix" is "/usr" by default.
It can be set optionally when calling "./configure" by typing "./configure --prefix=/home/login" for example.
This allows installation as non-root for example. ;)

Let's take a look at the glib-2.0.pc file used by when you use the "pkg-config --modversion glib-2.0" command:
```
>cat /usr/lib/pkgconfig/glib-2.0.pc
```

```
prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
includedir=${prefix}/include

glib_genmarshal=glib-genmarshal
gobject_query=gobject-query
glib_mkenums=glib-mkenums

Name: GLib
Description: C Utility Library
Version: **2.13.2**
Libs: -L${libdir} -lglib-2.0  
Cflags: -I${includedir}/glib-2.0 -I${libdir}/glib-2.0/include 
```

The error message says:
>  'pkg-config --modversion glib-2.0' returned 2.12.12, but GLIB (2.12.11)
*** was found! 
I know where 2.12.12 comes from, but not 2.12.11.
However, I suspect that it's simply the version found when following the libglib-2.0.so link.

Thus the potential solutions to your problem:
_POTENTIAL SOLUTIONS:_

[B][COLOR="Red"]I assume here that libglib-2.0.so links to libglib-2.0.so.2.12.11 instead of libglib-2.0.so.2.12.12.
Use ```
ls -l /usr/lib/libglib*
``` to find out what it should link to in your case.[/COLOR][/B]

**Solution 1: remove older library**
```
rm /usr/lib/libglib-2.0.so.2.12.11
```

**Solution 2: relink libglib-2.0.so**
```
cd /usr/lib
rm libglib-2.0.so
ln -s libglib-2.0.so.2.12.12 libglib-2.0.so
```

_notes:_
-solution 1 probably requires to relink too. But since the error message suggests a simple removal...

-You should search for parts of your error message in your configure file eventually.
That way you might find out where the second version number comes from.
I don't know why, but I haven't been able to find it in my configure files.

---

### Post by asymmetric on 2007-06-19
wow.. what an answer :)

---

