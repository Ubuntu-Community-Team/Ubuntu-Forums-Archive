---
title: "From tar.gz to working Balsa"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Dutch on 2006-06-16
Hi downloaded the tar.gz file for Balsa (newer version then with Synaptic.

But I'm stuck with the make en make install



What went wrong ?

---

### Post by th3james on 2006-06-16
You need a C compiler installed (GCC should do it). Also, your username doesnt seem to be a 'sudoer'

---

### Post by loell on 2006-06-16
you should 

sudo apt-get install build-essential

---

### Post by Dutch on 2006-06-16
[QUOTE=loell]you should 

sudo apt-get install build-essential[/QUOTE]

Ok I dit both :-)
The make and sudo make install went ok I gues.

And the version of Balsa stays 2.3.8
while it should be 2.3.12 !

How can I start the new version ?

---

### Post by Patrix on 2006-06-16
Enter the command "which balsa" to know the version you're running.
If you want to run the newly compiled version, either enter the full path for executable, or enter ./balsa if in the right directory, or else do a "make install" and it will probably go in /usr/local/bin and come first in your $PATH.

---

### Post by Dutch on 2006-06-16
[QUOTE=Patrix]Enter the command "which balsa" to know the version you're running.
If you want to run the newly compiled version, either enter the full path for executable, or enter ./balsa if in the right directory, or else do a "make install" and it will probably go in /usr/local/bin and come first in your $PATH.[/QUOTE]


Ok I'll explain some more.
I've downloaded the file
```

gmime-2.1.19.tar.gz  from:

```
from
```

http://balsa.gnome.org/download.html

```
then I 
make

and 

make install

```

paulaccount@PaulIBM:~/Desktop$ cd gmime-2.1.19
paulaccount@PaulIBM:~/Desktop/gmime-2.1.19$ ls
acconfig.h     configure        gmime-config.in  libtool      src
aclocal.m4     configure.in     gmimeConf.sh     ltmain.sh    stamp-h1
AUTHORS        COPYING          gmimeConf.sh.in  Makefile     tests
ChangeLog      depcomp          gmime.spec       Makefile.am  TODO
config.guess   docs             gmime.spec.in    Makefile.in  util
config.h       examples         gtk-doc.make     missing      zenprofiler.h
config.h.in    gmime            iconv-detect.c   mono         zentimer.h
config.log     gmime-2.0.pc     iconv-detect.h   NEWS
config.status  gmime-2.0.pc.in  INSTALL          PORTING
config.sub     gmime-config     install-sh       README
paulaccount@PaulIBM:~/Desktop/gmime-2.1.19$

```

I think the Balsa file is called gmime-2.1.19
But when I start that file, he says:
```

paulaccount@PaulIBM:~/Desktop/gmime-2.1.19$ gmime-2.1.19
bash: gmime-2.1.19: command not found
paulaccount@PaulIBM:~/Desktop/gmime-2.1.19$

```

Ok, st*pid me :-)
I see I took the wrong download ! try again with the balsa-2.3.12.tar.bz2
file !

---

### Post by loell on 2006-06-16
perhaps try uninstalling the previous balsa via synaptic, uncheck it there and click update, then try compilation process again, "make", "sudo make install"

then try executing balsa, and see if there is any difference..

---

### Post by loell on 2006-06-16
"I think the Balsa file is called gmime-2.1.19
But when I start that file, he says:
Code:

paulaccount@PaulIBM:~/Desktop/gmime-2.1.19$ gmime-2.1.19 bash: gmime-2.1.19: command not found paulaccount@PaulIBM:~/Desktop/gmime-2.1.19$"




i think its

cd paulaccount@PaulIBM:~/Desktop/gmime-2.1.19$"

then

./gmime


but i coul be wrong though...

---

### Post by Dutch on 2006-06-16
[QUOTE=loell]perhaps try uninstalling the previous balsa via synaptic, uncheck it there and click update, then try compilation process again, "make", "sudo make install"

then try executing balsa, and see if there is any difference..[/QUOTE]

Ok the correct file found and make worked ok.
Then I did .configure with this result:
```

checking for BALSA... configure: error: Package requirements (
glib-2.0
gtk+-2.0 >= 2.4
gmime-2.0 >= 2.1.9
libgnome-2.0 libgnomeui-2.0
   gnome-vfs-2.0 gnome-vfs-module-2.0 libbonobo-2.0
   libgnomeprint-2.2 >= 2.1.4 libgnomeprintui-2.2 >= 2.1.4
) were not met:

No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found
No package 'libbonobo-2.0' found
No package 'libgnomeprint-2.2' found
No package '' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BALSA_CFLAGS
and BALSA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

paulaccount@PaulIBM:~/Desktop/balsa-2.3.12$

```

I've looked with Synaptic and :
- libgnome-2.0 
- libgnomeui-2.0
- gnome-vfs-module-2.0
- libbonobo-2.0
- libgnomeprint-2.2
- libgnomeprint-2.2

= not installed but also not on the  Synaptic list.
 

libgnome2-vfs-perl is installed with Synaptic (not the correcty one ?) but the gnome-vfs-2.0 is not listed there.

Could u look at:
[http://balsa.gnome.org/download.html](http://balsa.gnome.org/download.html)

Must I download al the other 
```

# libesmtp-1.0.3r1-1.i386.rpm with corresponding libesmtp-1.0.3r1-1.src.rpm. Source tarball is available from libesmtp site.
# gmime-2.1.19.tar.gz on the GMIME site (check for the latest version).

```

files ?

---

### Post by loell on 2006-06-16
now things get complex when those dependencies aren't in the repository
you could also compile them, but i haven't have any successes in those instances

---

