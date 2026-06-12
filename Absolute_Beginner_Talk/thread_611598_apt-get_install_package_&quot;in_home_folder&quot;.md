---
title: "apt-get install package |&quot;in home folder&quot;"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-11-13
how can i install a package(like java,ruby ,etc...) in home folder only ?
so i can add PATH in "/home/username/.bashrc" to run those package binaries.
actually i am working in a server ,and i don't have root access.

---

### Post by mcduck on 2007-11-13
You can't.

If you manage to find a version of the programs you need that comes as a simple, extractable archive with  no need for actually installing anything, you can put it in your home. But apart from that you need to install things where they are supposed to go, and for that you need root privileges.

You should ask the administrator of the server if he could install the applications/tools you need, or to give you privileges to do that yourself.

Limiting what normal users can do on a machine is one of the basics of the security in Linux/Unix systems.

---

### Post by mokkai on 2007-11-13
thank you for your reply. 

actually i want to install ruby 1.8.6, so i download and extract it in
"/home/username/packages/ruby1.8.6"
in README file ,the instaruction to install is shown below 
---------------------------------------------------------------------------------
This is what you need to do to compile and install Ruby:
  1. If ./configure does not exist or is older than configure.in,
     run autoconf to (re)generate configure.
  2. Run ./configure, which will generate config.h and Makefile.
  3. Edit defines.h if you need.  Usually this step will not be needed.
  4. Remove comment mark(#) before the module names from ext/Setup (or
     add module names if not present), if you want to link modules
     statically.
     If you don't want to compile non static extension modules
     (probably on architectures which does not allow dynamic loading),
     remove comment mark from the line "#option nodynamic" in
     ext/Setup.
  5. Run make.
  6. Optionally, run 'make test' to check whether the compiled Ruby
     interpreter works well.  If you see the message "test succeeded",
     your ruby works as it should (hopefully).
  7. Run 'make install'
  You may have to be a super user to install ruby.
---------------------------------------------------------------------------

how can i install this in home path ? any idea ......

and when i execute  "./configure"
the output is 
---------------------------------------------------------------------
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
---------------------------------------------------------------------

what package should i install to solve this error?

---

### Post by mcduck on 2007-11-13
'build-essential' is the package that includes everything needed for compiling. But you can't install that one without super user privileges.

The stuff that build-essential installs are libc6-dev, gcc, g++, make and dpkg-dev.

I don't know how to change the code to install into another place, and actually I doubt that such things as Ruby would even work correctly that way.

---

### Post by eldepeche on 2007-11-13
This is possible, as long as the partition containing your home directory isn't mounted noexec, which it isn't, since you were able to run the configure script. You won't be able to use APT, but if you're only going to install a couple things, it could work.

What OS is running on the server? Who controls it? It appears that there is a problem with the version of GCC on the server. It isn't too hard to maintain a few programs and libraries in your home directory; at worst, you have to add some directories to PATH, and add extra options when installing software. For example, you would want to run 
```
./configure --prefix=$HOME <whatever other options>
``` to install Ruby.

BUT, maintaining your own copy of GCC in your home directory is going to be a royal pain.

---

