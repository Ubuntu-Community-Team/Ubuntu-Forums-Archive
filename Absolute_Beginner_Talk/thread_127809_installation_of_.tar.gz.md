---
title: "installation of .tar.gz"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by bountonw on 2006-02-09
I read the great installation guide here along with searching numerous threads.
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

Most threads teach how to install using synaptic or sudo apt-get.  Several mention how to dpkg .deb packages.  I really appreciate the search tool, but still can't find what I am looking for.  I thought I found it earlier only to have the power go out and have to reboot.  Now I can't remember the search I did and can't find the thread.

I am learned a lot, but never quite enough to do what I want to do!!

I have a CD with educational software on it.  It is a cover CD to a linux magazine.  All of the files are .tar.gz  I want to install most of them on my computer.  I am starting with the first one littlewizard.  I managed to figure out how to unzip the thing using
tar -zxvf littlewizard.blah
in order to do this, I needed to use the chmod command to give me permission to do this.

I then copied it to /opt

after cd to /opt/littlewizard.blah, I ran  ./configure as per above link and the INSTALL pages in the folder only to   get the following error messages.

> ton@wmien01:/opt/littlewizard-1.0.1$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for awk... awk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
ton@wmien01:/opt/littlewizard-1.0.1$


I tried to read the  config.log located here /var/log/base-config.log [I found it by using the locate command]

using the cat command I got only 1 inch of blue screen with "Ubuntu Configuration" written in the middle.

I am sure that I am doing something wrong.  Please help.
[I am trying to be as detailed as possible for several reasons.  1. I hope that it will aid whoever will answer this in diagnosing the problem, 2. If there are other newbies like myself out there in the universe, they can learn from my mistakes and also follow the steps better.]

---

### Post by o_fortuna on 2006-02-09
[QUOTE=bountonw]I read the great installation guide here along with searching numerous threads.
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

Most threads teach how to install using synaptic or sudo apt-get.  Several mention how to dpkg .deb packages.  I really appreciate the search tool, but still can't find what I am looking for.  I thought I found it earlier only to have the power go out and have to reboot.  Now I can't remember the search I did and can't find the thread.

I am learned a lot, but never quite enough to do what I want to do!!

I have a CD with educational software on it.  It is a cover CD to a linux magazine.  All of the files are .tar.gz  I want to install most of them on my computer.  I am starting with the first one littlewizard.  I managed to figure out how to unzip the thing using
tar -zxvf littlewizard.blah
in order to do this, I needed to use the chmod command to give me permission to do this.

I then copied it to /opt

after cd to /opt/littlewizard.blah, I ran  ./configure as per above link and the INSTALL pages in the folder only to   get the following error messages.



I tried to read the  config.log located here /var/log/base-config.log [I found it by using the locate command]

using the cat command I got only 1 inch of blue screen with "Ubuntu Configuration" written in the middle.

I am sure that I am doing something wrong.  Please help.
[I am trying to be as detailed as possible for several reasons.  1. I hope that it will aid whoever will answer this in diagnosing the problem, 2. If there are other newbies like myself out there in the universe, they can learn from my mistakes and also follow the steps better.][/QUOTE]
If you want to compile, there's a bunch of stuff you'll want to install from Synaptic/apt-get. Try:
```
sudo apt-get install build-essential
```
This will install the GNU Compiler Collection (gcc) which will let you compile. Now you should be able to ./configure without a problem.

---

### Post by engla on 2006-02-09
It might happen that the ./configure script tells you something's wrong -- that's part of its job -- first thing you need is the compiler that the above post with that above command will install for you. This is what all packages of this type need.

But it might also be the case that this specific needs [dependencies]. In that case your script might say "Library libgtkpod (or anything else!) not found" or something similar. Then you have to find this package first, before you can compile and install the package. If everything is easy, you should be able to find all those extra dependencies with synaptic.

---

### Post by bountonw on 2006-02-09
Thank you both.  Yes, there are dependencies.

> checking for gtk+-2.0 gdk-2.0... Package gtk+-2.0 was not found in the pkg-confi g search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 gdk-2.0) not met; consider adju sting the PKG_CONFIG_PATH environment variable if your libraries are in a nonsta ndard prefix so pkg-config can find them.
ton@wmien01:/opt/littlewizard-1.0.1$


I don't know how to change the PATH, and "gtk+-2.0" doesn't appear to be in Synaptic.  There is a lot of gtk things there and most of them are already installed.  Now what?  I am I barking up the wrong tree.  My short term goal is to be able to install .tar.gz files with ease (My children are wanting to play on Daddy's computer and I can't install the software:) I alsohave a computer in the jungle without internet access that I will migrate to linux in a few months.)  Long term goals is to be comfortible enough to help our local school in their migration to linux.

---

### Post by lol on 2006-02-10
You need some librairies to compile your program. When those are not present, you will most of the time have error complaining about a missing file. That's always a great help, because if you know the name a file, you can easily find which package can provide it, and simply install the required package...

Here, 'configure' is looking for a file called 'gtk+-2.0.pc'. To know which package provides this file, you can either use this site: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) or use apt-file (first install it):
```
apt-get install apt-file
apt-file update
```
and finally:
```
apt-file search gtk+-2.0.pc
libgtk+2.0-directfb-udeb-dev: usr/lib/udeblib/pkgconfig/gtk+-2.0.pc
libgtk2.0-dev: usr/lib/pkgconfig/gtk+-2.0.pc

```
The package you should installed in this case is probably libgtk2.0-dev...

Another tip: when you will understand how to compile the program, I strongly suggest that you use 'checkinstall' to build a package that will be easy to remove later...

Good luck.

---

### Post by linuxnovice on 2006-02-10
Hello,
Well I dont know whether this helps...But this is what I do. First download the .tar.gz file to somewhere (I usually download it onto /opt). Then go the directory via terminal.
Then,
sudo tar xvzf <package>.tar.gz
This will unpack it. Then go to the directory that the tar command created and look whats in there. If you see a configure executable then :
./configure
make 
make install
(all with sudo ofcourse)

If there is no configure then make and make install would probably do.
I hope this helps...if it doesnt..good luck finding what you are looking for.
Linuxnovice.

---

### Post by bountonw on 2006-02-10
Installed the above packages.  Now I have a new problem.  Will try installing the suggested lib.

> checking PACKAGE_LIBS... -lgtk-x11-2.0 -latk-1.0 -lgdk-x11-2.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXf ixes -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lXrender -lX11 -ldl
checking for libxml-2.0 >= 2.4... Package libxml-2.0 was not found in the pkg-co nfig search path. Perhaps you should add the directory containing `libxml-2.0.pc ' to the PKG_CONFIG_PATH environment variable No package 'libxml-2.0' found
configure: error: Library requirements (libxml-2.0 >= 2.4) not met; consider adj usting the PKG_CONFIG_PATH environment variable if your libraries are in a nonst andard prefix so pkg-config can find them.


lol:
I don't know what you meant by checkinstall. I tried the man pages and don't see anything.

linuxnovice:
Thank you.  That makes sense.  Right now I am stuck at the ./configure stage as I think I have what they call dependencies.  (I think that is what you call it anyway.)

---

### Post by bountonw on 2006-02-10
I am not sure how to adjust the path and what they are even talking about.  

Using apt-file search libxml-2.0 I get the following.  

> libxml2-dev: usr/lib/pkgconfig/libxml-2.0.pc

I installed libxml2-dev with

```
 sudo apt-get install
```

Anyway, I think I get it now.  the "usr/lib/pkgconfig/libxml-2.0.pc is the destination where it will be installed.

I then followed all the steps
```
sudo ./configure
sudo make
sudo make install
```

Now I have no idea how to open the program!!!!!  Here is the folder contents

> ABOUT-NLS     AUTHORS       config.h.in    [COLOR="Lime"]config.sub[/COLOR]   [COLOR="RoyalBlue"] data  [/COLOR]   [COLOR="PaleGreen"]install-sh [/COLOR] [COLOR="PaleGreen"] ltmain.sh [/COLOR]  [COLOR="PaleGreen"] missing  [/COLOR]      [COLOR="RoyalBlue"]po   [/COLOR]     TODO
acconfig.h    ChangeLog     config.log     [COLOR="Lime"]configure    [/COLOR] depcomp [COLOR="RoyalBlue"] liblanguage[/COLOR]  Makefile     [COLOR="PaleGreen"]mkinstalldirs  [/COLOR]README
acinclude.m4 [COLOR="Lime"] config.guess [/COLOR][COLOR="Lime"] config.rpath [/COLOR]  configure.in [COLOR="RoyalBlue"] include [/COLOR] [COLOR="RoyalBlue"]liblw[/COLOR]        Makefile.am  NEWS           [COLOR="RoyalBlue"]src[/COLOR]
aclocal.m4    config.h      [COLOR="Lime"]config.status[/COLOR]  COPYING       INSTALL [COLOR="PaleGreen"] libtool [/COLOR]     Makefile.in  [COLOR="RoyalBlue"]pixmaps [/COLOR]       stamp-h1


That was hard work getting the colors in.  Hopefully someone can tell me what to do to open this program or at least where to look.  I read the README, but didn't see anything about starting the program.

---

### Post by Lord Illidan on 2006-02-10
Try running ```
littlewizard
``` from a terminal.

---

### Post by bountonw on 2006-02-10
I tried that first off, but didn't work. 

I did the whole install from terminal.  Kind of fun to watch all of the stuff screen by even though I am clueless to know what most of it means.  

Tried to <locate littlewizard>, but it only showed me the original tar.gz file.

---

### Post by lol on 2006-02-10
'make install' probably installed the program in /usr/local/bin. Check if this dir is in your path, with 'echo $PATH'

'locate' uses a database that you need to update first, with 'sudo updatedb'. Alternatively, you can find the location of the program with 'find / -name "littlewizard"'.

checkinstall is a nice tool that build a .deb package. That's much better than using 'make install', because you can then easilly remove the program. You first need to install it with 'apt-get install checkinstall'.
To use it, simply run 'checkinstall' instead of 'make install'. It can even take care of the compilation.

Another great tool you may find usefull is 'auto-apt', that can install the missing librairies when you are compiling a program.

You can probably find more about checkinstall and auto-apt in the forums...

---

### Post by bountonw on 2006-02-10
yes. program is in /usr/local/bin

but as an abreviation.

Thank you for your help.

---

