---
title: "Glade &amp; C++"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by TroyMW on 2006-01-12
I've been using Linux(Ubuntu) for only 2 months.  I'm trying to learn how to compile a Glade user interface with a C++ back end.  I can create a C program, but am having trouble creating a C++.  After I build the interface with the C++ option and go to the directory containing the Glade generated files I type 'sudo ./autogen.sh' and get the following output:

     Running glib-gettextize... Ignore non-fatal messages.
     Copying file mkinstalldirs
     Copying file po/Makefile.in.in

     Please add the files
       codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
       progtest.m4
     from the /usr/local/share/aclocal directory to your autoconf macro directory
     or directly to your aclocal.m4 file.
     You will also need config.guess and config.sub, which you can get from
     [ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

I can't find these files (codeset.m4...) in /usr/local/share/aclocal.  And the ftp link doesn't seem to be working.  Can anyone tell me where the may be?

Thanks in advance.

---

### Post by Jave27 on 2006-01-12
[QUOTE=TroyMW]After I build the interface with the C++ option and go to the directory containing the Glade generated files I type 'sudo ./autogen.sh' and get the following output:

     Running glib-gettextize... Ignore non-fatal messages.
     Copying file mkinstalldirs
     Copying file po/Makefile.in.in

     Please add the files
       codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
       progtest.m4
     from the /usr/local/share/aclocal directory to your autoconf macro directory
     or directly to your aclocal.m4 file.
[/QUOTE]

See [here]("http://www.nabble.com/Help-!!-error-on-running-autogen-.-t746847.html").  Looks like you need an updated autoconf/automake package.  Try "apt-cache search automake" to see what packages are available.

---

### Post by Strife on 2006-01-12
Also, when using Glade, you really shouldn't have it generating code for you anyway. All you really want to do with it is make the Glade XML file to use with your own code. The reason being that the whole advantage of using Glade is that it generates an XML file that defines the user interface, thus if you make minor changes, you can just load a new XML file and not have to recompile.

---

