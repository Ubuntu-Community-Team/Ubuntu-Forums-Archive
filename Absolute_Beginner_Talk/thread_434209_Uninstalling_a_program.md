---
title: "Uninstalling a program"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by joey_01122 on 2007-05-05
I am very new to Ubuntu and Linux in general.
I installed a program called "linuXtree" by downloading
a tarball file and extracting it, then changing to the
folder where the makefile is and installing it with the
make and make install commands.
Now I want to uninstall this program but when I use
the  command "sudo make uninstall" I get a message
"No rule to make target `uninstall'.  Stop."
Is there a relatively easy way to remove this application?

---

### Post by taurus on 2007-05-05
Did you run 

```
make install
```
as a regular user or as root?

Otherwise, try

```
./configure
make
sudo make uninstall
```

---

### Post by joey_01122 on 2007-05-05
> **taurus said:**
> Did you run 

```
make install
```
as a regular user or as root?

Otherwise, try

```
./configure
make
sudo make uninstall
```

I ran make and make install as root, this was an error on my part.

I tried the commands ./configure
                                    make
                                    sudo make install 
as root and as local user and I still get this error message:
 *** No rule to make target `uninstall'.  Stop.

---

### Post by taurus on 2007-05-05
Are you using the same version and unpack it in the same directory that you did before when you installed it?

---

### Post by joey_01122 on 2007-05-05
> **taurus said:**
> Are you using the same version and unpack it in the same directory that you did before when you installed it?

Yes, I used the same file and the same directory.

The file is called lxt-1.2.tgz
I moved it to a folder called lxtree
I changed to that folder and used the
command tar -xvf lxt-1.2.tgz to extract 
the files.  The files were extracted to a
subfolder called lxt.  I changed to /lxtree/lxt/
and typed make.
This is the output:
./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for initscr in -lncurses... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for unistd.h... (cached) yes
checking mntent.h usability... yes
checking mntent.h presence... yes
checking for mntent.h... yes
checking sys/mntent.h usability... no
checking sys/mntent.h presence... no
checking for sys/mntent.h... no
checking sys/mnttab.h usability... no
checking sys/mnttab.h presence... no
checking for sys/mnttab.h... no
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/mount.h usability... yes
checking sys/mount.h presence... yes
checking for sys/mount.h... yes
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking return type of signal handlers... void
checking for getmntent in -lsun... no
checking for getmntent in -lseq... no
checking for getmntent in -lgen... no
checking for getmntent... yes
checking type of getmntent function... BSD
checking for getcwd... yes
checking for mkdir... yes
checking for rmdir... yes
checking for strerror... yes
checking for lchown... yes
checking for statfs... yes
checking for statvfs... yes
checking for vsnprintf... yes
checking for vfprintf... yes
checking for snprintf... yes
checking if statvfs structure has f_frsize element... yes
checking for wgetbkgd... no
checking for regcmp in -lgen... no
checking for regcmp in -lintl... no
checking for regcmp in -lPW... no
checking for regcomp... using POSIX regcomp
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
make
make[1]: Entering directory `/xt2/lxt'
gcc -c -Wall -Wstrict-prototypes -g -O2  -O commands.c -o commands.o
gcc -c -Wall -Wstrict-prototypes -g -O2  -O compatible.c -o compatible.o
gcc -c -Wall -Wstrict-prototypes -g -O2  -O data.c -o data.o
gcc -c -Wall -Wstrict-prototypes -g -O2  -O gui.c -o gui.o
gui.c: In function &#8216;gui_printable&#8217;:
gui.c:1822: warning: pointer targets in assignment differ in signedness
gui.c:1831: warning: pointer targets in assignment differ in signedness
gui.c:1845: warning: pointer targets in assignment differ in signedness
gcc -c -Wall -Wstrict-prototypes -g -O2  -O main.c -o main.o
gcc -c -Wall -Wstrict-prototypes -g -O2  -O readconfig.c -o readconfig.o
gcc -c -Wall -Wstrict-prototypes -g -O2  -O readln.c -o readln.o
gcc -c -Wall -Wstrict-prototypes -g -O2  -O uid.c -o uid.o
gcc -c -Wall -Wstrict-prototypes -g -O2  -O view.c -o view.o
view.c: In function &#8216;view_openhelp&#8217;:
view.c:129: warning: pointer targets in assignment differ in signedness
view.c: In function &#8216;view_drawview&#8217;:
view.c:585: warning: pointer targets in passing argument 2 of &#8216;view_readbuffer_crunchcodes&#8217; differ in signedness
view.c:585: warning: pointer targets in passing argument 3 of &#8216;view_readbuffer_crunchcodes&#8217; differ in signedness
view.c:587: warning: pointer targets in passing argument 2 of &#8216;view_readbuffer&#8217; differ in signedness
gcc -c -Wall -Wstrict-prototypes -g -O2  -O edit.c -o edit.o
gcc -s -o lxt commands.o compatible.o data.o gui.o main.o readconfig.o readln.o uid.o view.o edit.o -lncurses
-rwxr-xr-x 1 joey joey142580 May  5 18:25 lxt
make[1]: Leaving directory `/lxtree/lxt'

From the lxtree/lxt folder I then ran sudo make install
this put a file called lxt in usr/local/bin.  I don't know what
other files where installed,  if any.

I then typed 

./configure      

 make       

sudo make install
again and got the message "*** No rule to make target `uninstall'. Stop."
yet another time.

These are the files in the folder I
extracted to:
aclocal.m4
all.h
bugs
Changes
chartest.txt
commands.c
commands.h
commands.o
compatible.c
compatible.h
compatible.o
config.h
config.h.in
config.log
config.status
configure
configure.in
COPYING
data.c
data.h
data.o
edit.c
edit.h
edit.o
gui.c
gui.h
gui.o
help.h
INSTALL
main.c
main.h
main.o
Makefile
Makefile.dist
Makefile.in
readconfig.c
readconfig.h
readconfig.o
readln.c
readln.h
readln.o
uid.c
uid.h
uid.o
view.c
view.h
view.o

---

### Post by taurus on 2007-05-05
The binary will be in /usr/local/bin; the libary will be in /usr/local/lib; the manpage will be in /usr/local/man; and the share stuff will be in /usr/local/share.

---

### Post by joey_01122 on 2007-05-06
> **taurus said:**
> The binary will be in /usr/local/bin; the libary will be in /usr/local/lib; the manpage will be in /usr/local/man; and the share stuff will be in /usr/local/share.

Thanks for assisting me in this.  I didn't see anything in /usr/local/lib or /usr/local/man but because
I mistakenly typed "sudo make" instead of "make" on my first installation I don't know if any library
files might have gone to another folder.
Would a package like "deborphan" be helpful at all in tracking down any possible stray library files?
Again,  thanks for your help.

---

### Post by taurus on 2007-05-06
If you look at the INSTALL, it will tell you where everything will be installed.  Otherwise, look at Makefile to see the destinations.

---

