---
title: "Need elmer help to install fldigi. Thanks"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by alaskagene on 2008-04-07
I found my way to the install page but I am unable to follow the instructions.  I am stuck here:

  Now navigate to the location of the downloaded archive, then
Code:

tar -xvzf hamlib-1.2.6.1.tar.gz
cd hamlib-1.2.6.1
./configure
make
sudo make install


Need know how to navigate as directed.  

Appreciate any advice or help................

Thanks in advance

AL7KH in Ketchikan, Alaska

---

### Post by Michael.Godawski on 2008-04-07
You have to know where you have downloaded the archive. Lets say the desktop.
To navigate to your desktop use the commands
```
cd
```
and 
```
ls
```

With cd you can change the directory. With ls you can list all folder in a directory.

```
cd Desktop
```

Linux is case sensitive. So Desktop is not the same as desktop.

---

### Post by mikewhatever on 2008-04-07
If the downloaded archive is in your home folder, you are already there, if on Desktop, then <cd ~/Desktop>.

---

### Post by alaskagene on 2008-04-07
Did the above as suggested. Installed the client program. 
I have two folders on the Desktop: hamlib-1.2.6.1 tar.gz and 
fltk-1.1.7-source.tar.gz.

Now what?

de AL7KH

---

### Post by mikewhatever on 2008-04-07
You might want to tell more about the program. What is it? What is it supposed to do? Does it have a name? A web site? I know nothing about it.
Are these folders or archives on your Desktop?

---

### Post by alaskagene on 2008-04-07
Mike,
the program is to be used to operate a ham radio in various digital modes. The name of the program is FLDIGI. 

I am attempting to follow the install instruction from:

    [http://ubuntuforums.org/showthread.php?t=380639](http://ubuntuforums.org/showthread.php?t=380639)

This is a 'how to' tutorial.  I am new to Ubuntu so am having  a little difficulty in following the cookbook.  I guess the  best way  for me is to just jump in with both feet and learn as I
go. I am becoming more familar with the terminal program but some instructions assume a lot of prior knowledge. 

I appreciate the prompt reply and help from you guiys (and gals?). 

de AL7KH in Ketchikan, Alaska

---

### Post by alaskagene on 2008-04-07
I previously posted:

tar -xvzf hamlib-1.2.6.1.tar.gz
cd hamlib-1.2.6.1
./configure
make
sudo make install

Changed to directory from desktop to Desktop and was successful down to the third line. Entering 'make' into the terminal line, the following appeared:

gene@gene-desktop:~/Desktop/hamlib-1.2.6.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for gawk... (cached) mawk
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for rpmbuild... no
checking for egrep... grep -E
checking for AIX... no
checking for library containing strerror... none required
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc needs -traditional... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether user wants warnings... yes
checking whether gcc accepts -Wall... yes
checking whether g++ accepts -Wall... no
checking whether g++ accepts -Woverloaded-virtual... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking alloca.h usability... yes
checking alloca.h presence... yes
checking for alloca.h... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for memory.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking for stdlib.h... (cached) yes
checking values.h usability... yes
checking values.h presence... yes
checking for values.h... yes
checking rpc/rpc.h usability... yes
checking rpc/rpc.h presence... yes
checking for rpc/rpc.h... yes
checking rpc/rpcent.h usability... no
checking rpc/rpcent.h presence... no
checking for rpc/rpcent.h... no
checking net/errno.h usability... no
checking net/errno.h presence... no
checking for net/errno.h... no
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for unistd.h... (cached) yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking sys/ioccom.h usability... no
checking sys/ioccom.h presence... no
checking for sys/ioccom.h... no
checking sgtty.h usability... yes
checking sgtty.h presence... yes
checking for sgtty.h... yes
checking term.h usability... no
checking term.h presence... no
checking for term.h... no
checking termio.h usability... yes
checking termio.h presence... yes
checking for termio.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking linux/ppdev.h usability... yes
checking linux/ppdev.h presence... yes
checking for linux/ppdev.h... yes
checking linux/parport.h usability... yes
checking linux/parport.h presence... yes
checking for linux/parport.h... yes
checking linux/ioctl.h usability... yes
checking linux/ioctl.h presence... yes
checking for linux/ioctl.h... yes
checking dev/ppbus/ppi.h usability... no
checking dev/ppbus/ppi.h presence... no
checking for dev/ppbus/ppi.h... no
checking dev/ppbus/ppbconf.h usability... no
checking dev/ppbus/ppbconf.h presence... no
checking for dev/ppbus/ppbconf.h... no
checking for inttypes.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for sys/types.h... (cached) yes
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
checking for winioctl.h... no
checking for winbase.h... no
checking for getopt... yes
checking for getopt_long... yes
checking for usleep... yes
checking for gettimeofday... yes
checking for struct timezone... yes
checking for ssize_t... yes
checking for getopt... (cached) yes
checking for getopt_long... (cached) yes
checking for usleep... (cached) yes
checking for gettimeofday... (cached) yes
checking for Sleep... no
checking POSIX termios... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... (cached) yes
checking return type of signal handlers... void
checking for siginfo_t... yes
checking for sin... no
checking for main in -linet... no
checking for connect... yes
checking for gethostbyname... yes
checking for syslog in -lsyslog... no
checking for atexit... yes
checking for snprintf... yes
checking for select... yes
checking for memmove... yes
checking for memset... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strdup... yes
checking for strerror... yes
checking for strrchr... yes
checking for strstr... yes
checking for strtol... yes
checking for cfmakeraw... yes
checking for setitimer... yes
checking for ioctl... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for vprintf... yes
checking for _doprnt... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
gene@gene-desktop:~/Desktop/hamlib-1.2.6.1$ make
make: *** No targets specified and no makefile found.  Stop.
gene@gene-desktop:~/Desktop/hamlib-1.2.6.1$ make
make: *** No targets specified and no makefile found.  Stop.
gene@gene-desktop:~/Desktop/hamlib-1.2.6.1$ sudo make install
make: *** No rule to make target `install'.  Stop.
gene@gene-desktop:~/Desktop/hamlib-1.2.6.1$ 


BTW, Folders for fltk-1.1.7 and hamlib-1.2.6.1 are on the Desktop.

Gene in Ketchikan

---

### Post by mikewhatever on 2008-04-07
Frankly, this is not the best program to start with. It looks like the ./configure process ended with an error, that's why you don't get the make file. I've no idea what the error means, hope someone more advanced will help you.
> checking how to run the C++ preprocessor... /lib/cpp
[COLOR="Red"]configure: error: C++ preprocessor "/lib/cpp" fails sanity check[/COLOR]
See `config.log' for more details.

---

### Post by mali2297 on 2008-04-07
Have you installed **build-essential**?
```

sudo apt-get install build-essential

```

---

### Post by Sef on 2008-04-07
Have you installed build-essential?

If not, then follow these commands:

```
sudo apt-get update
```

```
sudo apt-get install build-essential
```

Then follow the directions for the program again.

---

### Post by alaskagene on 2008-04-07
Executed the essential-build command succesfullly.

Began again from the start and it appears all went well.

Reached another sticking point:

     gene@gene-desktop:~$ cd Desktop
gene@gene-desktop:~/Desktop$ cd fltk-1.1.7-source
bash: cd: fltk-1.1.7-source: No such file or directory
gene@gene-desktop:~/Desktop$ 


Note in line three the 'bash' comment.  FLTK is in the Desktop.  Is the command correct as copied or do I need to change it to arrive at the correct directory???

gene in Ketchikan

---

### Post by mali2297 on 2008-04-08
It's an error in the instructions, the extracted folder is called **fltk-1.1.7**. Try this:
```

sudo apt-get install xorg-dev
cd ~/Desktop
tar xvzf fltk-1.1.7-source.tar.gz
cd fltk-1.1.7
./configure --enable-threads --enable-xft --enable-localjpeg --enable-localpng --enable-localzlibelease
make
sudo checkinstall

```
Then continue with fldigi.

If you plan to upgrade your version of Ubuntu, then fldigi is available in both gutsy and hardy repositories without the need to compile from source.

---

### Post by alaskagene on 2008-04-08
Just a short note to thank all for helping me install fldigi.  You people are great. Thanks for taking the time and being there.

I did a search and found the downloaded programs in the /usr directory.  The programs are on the hard disk but spread around. Some in /usr and some in Desktop. Next project is to learn how to move all the programs and files into a single directory (if that is necessary).

CUL

Gene in Ketchikan

---

### Post by alaskagene on 2008-04-09
My previous post apparently did not get through.  Thanks, all of you, for your help.  Quick replies and quality expert help.

The program was successfully installed.  It took me some time to find it. 
Last nite I ran some files into the mic port from my other laptop.  CW and RTTY worked well.  

I don't have the CAT cable yet so I won't know about TX until then.

Many thanks for all the help.

Gene in Ketchikan

---

