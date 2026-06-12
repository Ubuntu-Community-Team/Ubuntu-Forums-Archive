---
title: "Cannot compile against GLib or Gtk+"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-03-02
Hi everyone.
It seems there are lots of problems with updating Gtk-Gnutella.
I have another, related, one.
```
ERROR: Cannot compile against GLib.
ERROR: Cannot compile against Gtk+.
```
I've searched thru the posts here and tried every fix mentioned, downloaded libraries, incl ```
libxml2 (http://www.xmlsoft.org/) to compile Gtk-Gnutella
```. and ```
zlib http://www.zlib.net/) to compile Gtk-Gnutella
``` from the original error message.
I've done```
 sudo ldconfig
``` and also restarted.
I was hoping that this ```
omar@Rubaiyat-desktop:~$ ./configure.gnu -ders
``` would run all defaults as I have no idea what are the right settings/answers.
Obviously this query ```
Which compiler compiler (yacc) shall I use?
``` is critical and I don't know the right answer. Tried zlib, gcc.
Yes, I'm out of my depth, to put it nicely. Here's hoping some EASY answer will occur to those in their depth.

Gibbering wreck :confused: 
I didn't post the entire output as its loooonng!

---

### Post by lloyd_b on 2007-03-02
The command you want is
```
./Configure -Oders
```

This will provide reasonable defaults for almost all of the options.  The one option that it may still hang on is:
```
Which compiler compiler (yacc) shall I use?
```

In which case you should try "yacc" (Yes, it's that simple).

If you get errors involving GTK or Glib, then verify that you have the GTK/Glib development packages installed ("libgtk1.2-dev" and "libglib1.2-dev", or "libgtk2.0-dev" and "libglib2.0-dev").  These can be downloaded/installed via Synaptic, or in a terminal window type
```
sudo apt-get install {package}
```

Lloyd B.

---

### Post by carloslosgrande on 2007-03-02
Hi Lloyd,
 I tried 'yacc' the very first time, and the libraries that were missing, I have since installed (synaptic) and retried the configure (several times).
I've just tried```
 ./configure.gnu -Oders
``` with the same result.
Thanks,
still gibbering.

---

### Post by lloyd_b on 2007-03-02
First off, I've never tried the "configure.gnu" - I've always used "Configure".  Please try it instead and see what errors it produces.

I just checked - I've been specifying "yacc" all along, but I don't even have it installed on my system!  I'm guessing that it's an obsolete option, and probably doesn't matter (I'll post a question regarding it on the developers list for confirmation).

As for the errors, could you post the actual errors, and the 10-15 lines preceeding them?  The errors you list don't really mean a lot, and I'm hoping that there will be something that provides a better clue in those preceeding lines.

Lloyd B.

---

### Post by carloslosgrande on 2007-03-03
Hi Lloyd, the reason I configured that way is that is the file that comes with it, ie I just type in conf hit tab and it fills in the rest from that directory.
I just tried your suggestion and it says 'no such file'
So here is the complete output, I have looked thru it but am no more enlightened than not looking.

omar@Rubaiyat-desktop:~$ cd gtk-gnutella-0.96.3/
omar@Rubaiyat-desktop:~/gtk-gnutella-0.96.3$ ./configure.gnu -Oders
sh ./Configure -ds -e -Oders
First let's make sure your kit is complete.  Checking...
Would you like to see the instructions? [n]
Locating common programs...
Checking compatibility between /bin/echo and builtin echo (if any)...
Symbolic links are supported.
Checking how to test for symbolic links...
Your builtin 'test -h' may be broken.
Trying external '/usr/bin/test -h'.
You can test for symbolic links with '/usr/bin/test -h'.
Good, your tr supports [:lower:] and [:upper:] to convert case.
Using [:upper:] and [:lower:] to convert case.
Operating system name? [linux]
Operating system version? [2.6.15-28-386]
Is this producing an official build [n]
Run without any GUI interface [n]
Enable remote control service [y]
Use which GTK toolkit (1 or 2) [1]
Do you expect to run these scripts and binaries on multiple machines? [n]
Installation prefix to use? (~name ok) [/usr/local]
AFS does not seem to be running...
Pathname where the public executables will reside? (~name ok)
[/usr/local/bin]
System manual is in /usr/share/man/man1.
Where do the manual pages (source) go? (~name ok) [/usr/share/man/man1]
Pathname where the private library files will reside? (~name ok)
[/usr/local/lib/gtk-gnutella]
Directories to use for library searches? [/usr/local/lib /lib /usr/lib]
What is the file extension used for shared libraries? [so]
Use which C compiler? [cc]
Checking for GNU cc in disguise and/or its version number...
Now, how can we feed standard input to your C preprocessor...
What optimizer/debugger flag should be used? [-O2 -g]
Any additional cc flags? [-W -Wall -Wformat=2 -Wshadow -I/usr/local/include]
Let me guess what the preprocessor flags are...
Any additional ld flags (NOT including libraries)? [-L/usr/local/lib]
Checking your choice of C compiler and flags for coherency...
Checking for optional libraries...
Which libraries to use? [-lz -lresolv]
Checking for GNU C Library...
/usr/bin/nm probably won't work on the GNU C Library.
Shall I use nm to extract C symbols from the libraries? [n]
gettext() found.
Computing filename position in cpp output for #include directives...
<libintl.h> found.
You have NLS support.
Shall I enable NLS [y]
Where do you want to put the localization files? (~name ok)
[/usr/share/locale]
Checking whether your compiler can handle __attribute__ ...
bcopy() found.
bind_textdomain_codeset() found.
Checking whether cc has __builtin_popcount...
Checking to see if your C compiler knows about "const"...
Checking how we can gather information about dbus...
You've don't seem to have dbus installed?
Checking whether /dev/poll is available ...
Checking whether epoll() is available ...
Shall I enable "fast assertions" [y]
Shall I enable the -momit-leaf-frame-pointer flag [y]
Added -momit-leaf-frame-pointer to the cc flags.
Checking whether getaddrinfo() can be used ...
Checking whether geteuid() is available ...
<net/if.h> found.
Checking whether getifaddrs() is available ...
getinvent() NOT found.
getdtablesize() found.
Checking whether getuid() is available ...
Checking how we can gather information about GNU TLS...
You've don't seem to have GNU TLS installed?
herror() found.
hstrerror() found.
initstate() found.
<netinet/in.h> found.
<netinet/ip.h> found.
Checking for IP TOS (Type of Service) support...
Checking whether IPv6 can be used ...
Enable IPv6 support [y]
isascii() found.
Checking whether the member "udata" of "struct kevent" is an integer ...
Checking whether kqueue() is available ...
Checking how we can gather information about libxml2...
lstat() found.
madvise() found.
memalign() found.
memcpy() found.
mmap() found.
Checking whether "struct msghdr" has a member "msg_flags"...
<sys/file.h> defines the O_* constants...
and you have the 3 argument form of open().
poll() found.
Checking whether posix_memalign() is available ...
pread() found.
preadv() NOT found.
pwrite() found.
pwritev() NOT found.
random() found.
getrusage() found.
Checking whether SA_INTERRUPT is available in <signal.h>...
sendfile() found.
Checking whether setproctitle() is available ...
sigaction() found.
POSIX sigsetjmp found.
Checking whether socker_get() is available...
Seems like socker is missing: privileged ports won't be usable.
Checking how we can gather information about SQLite...
You've don't seem to have SQLite installed?
srandom() found.
Using <string.h> instead of <strings.h>.
strchr() found.
strlcat() NOT found.
strlcpy() NOT found.
sysctl() found.
<sys/times.h> found.
times() found.
What type is returned by times() on this system? [clock_t]
Figuring out host name...
Your host name appears to be "Rubaiyat-desktop". Right? [y]
uname() found.
usleep() found.
Checking to see if your C compiler knows about "volatile"...
vsnprintf() found.
<unistd.h> found.
Checking whether we need flags for large file support...
You're not natively compiling for large file, fixing...
Checking alignment constraints...
Doubles must be aligned on a how-many-byte boundary? [4]
Checking to see how your cpp does stuff like catenate tokens...
I can't determine whether signal handler returns void or int...
What type does your signal handler return? [void]
Figuring out the flag used by open() for non-blocking I/O...
Let's see what value errno gets from read() on a O_NONBLOCK file...
Compiling for GTK 1: we'll use 'glade'.
Checking how we can gather information about glib...
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
*** WARNING:
*** Cannot compile against glib version ''
***
Checking how we can gather information about GTK+...
sh: gtk-config: command not found
sh: gtk-config: command not found
sh: gtk-config: command not found
*** WARNING:
*** you asked for GTK+ 1, I found
***
sh: gtk-config: command not found
sh: gtk-config: command not found
sh: gtk-config: command not found
sh: gtk-config: command not found
sh: gtk-config: command not found
sh: gtk-config: command not found
*** WARNING:
*** Cannot compile against Gtk+ version ''
***
Figuring out my version number...
Looking for a BSD-compatible install program...
Which install program shall I use? (~name ok) [/usr/bin/install]
Ok, let's see how we can create nested directories...
Which memory models are supported? [none]
Checking if your /usr/bin/make program sets $(MAKE)...
Checking how to generate makefile dependencies on your machine...
Name of program to make makefile dependencies? (~name ok)
[/home/omar/gtk-gnutella-0.96.3/mkdep]
Let's see whether your /usr/bin/msgmerge supports the --update flag...
Checking out function prototypes...
Checking how to generate random libraries on your machine...
Checking to see how well your C compiler groks the void type...
Which compiler compiler (yacc) shall I use? yacc
Any additional yacc flags? [none]
<arpa/inet.h> found.
<dirent.h> found.
<sys/file.h> found.
We'll be including <sys/file.h>.
<fcntl.h> found.
We don't need to include <fcntl.h> if we include <sys/file.h>.
<ifaddrs.h> found.
<inttypes.h> found.
<invent.h> NOT found.
<langinfo.h> found.
<libcharset.h> NOT found.
<netdb.h> found.
<pwd.h> found.
<regex.h> found.
<stdarg.h> found.
<varargs.h> found.
We'll include <stdarg.h> to get va_dcl definition.
<stdlib.h> found.
<sys/mman.h> found.
<sys/param.h> found.
<sys/resource.h> found.
<sys/sendfile.h> found.
<sys/socket.h> found.
<sys/stat.h> found.
<sys/sysctl.h> found.
Testing to see if we should include <time.h>, <sys/time.h> or both.
We'll include <time.h>.
We'll include <sys/time.h>.
<sys/types.h> found.
<sys/un.h> found.
<sys/utsname.h> found.
deflate() found.
inflate() found.
<zlib.h> found.
Checking whether we can use sendfile() with large file support...
Checking whether -mieee should be used...

Feature Summary (Version 0.96.3):
-------------------------------------------------
GLib version                       : glib-1.x
GUI front-end                      : GTK1
GNU TLS support                    : no
IPv6 support                       : yes
NLS (Native Language Support)      : yes
Fast assertions                    : yes
DBus support (experimental)        : no
SQLite (experimental)              : no
Remote Shell Interface (deprecated): yes
-------------------------------------------------
ERROR: Cannot compile against GLib.
ERROR: Cannot compile against Gtk+.
omar@Rubaiyat-desktop:~/gtk-gnutella-0.96.3$

Hope you can see something,
Thanks for your trouble,
Carl.

---

### Post by lloyd_b on 2007-03-03
First off, ignore the "yacc" issue.  yacc is only required if you're doing development on certain parts of gtk-gnutella.  The files produced by it are included in the tarball or SVN tree, so for the ordinary user (or most developers, for that matter) yacc isn't required.

Second, I've never tried building gtk-gnutella from the tar.gz (I grab the most recent version from the SourceForge SVN repository).  I'm surpised that there's no "Configure", but that's probably a matter of choice by the person who created the tarball...

Finally:
```
Compiling for GTK 1: we'll use 'glade'.
Checking how we can gather information about glib...
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found
*** WARNING:
*** Cannot compile against glib version ''
***
Checking how we can gather information about GTK+...
sh: gtk-config: command not found
sh: gtk-config: command not found
sh: gtk-config: command not found
*** WARNING:
*** you asked for GTK+ 1, I found
***
sh: gtk-config: command not found
sh: gtk-config: command not found
sh: gtk-config: command not found
sh: gtk-config: command not found
sh: gtk-config: command not found
sh: gtk-config: command not found
*** WARNING:
*** Cannot compile against Gtk+ version ''
***
```

This says it all - you do NOT have the gtk 1.2 and glib 1.2 development packages installed.  If you did, then you would have the commands "glib-config" and "gtk-config" in your "/usr/bin" directory.

So, you need to install "libglib1.2-dev" and "libgtk1.2-dev".  If synaptic/apt-get shows that these are already installed, try removing them and then re-installing.

Lloyd B.

---

### Post by carloslosgrande on 2007-03-03
Lloyd, brilliant! thanks man, that was it alright. Its now configured!
Thanks again.
Carl.:guitar:

---

