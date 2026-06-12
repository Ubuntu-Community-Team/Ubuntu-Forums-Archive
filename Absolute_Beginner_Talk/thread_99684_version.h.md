---
title: "version.h"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-12-06
```
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel

```

what does this mean when doing a ./configure

---

### Post by amohanty on 2005-12-06
you need to do a:
```
sudo apt-get build-essential kernel-package linux-kernel-headers
```

I think you can leave out the kernel-package, but since I dont know what you are trying to install, its a safe bet.

HTH
AM

---

### Post by adduds on 2005-12-06
i'm trying to install the ALSA 1.0.10 drivers but when i type in

./configure it says

```
adduds@adtop:/etc/alsa/alsa-driver-1.0.10$ ./configure
./configure: line 88: conf16546.sh: Permission denied
./configure: line 89: conf16546.sh: Permission denied
chmod: cannot access `conf16546.sh': No such file or directory
./configure: line 201: conf16546.file: Permission denied
./configure: line 943: config.log: Permission denied

```

so then i sudo ./configure:

```
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

```

i have all the build essentials, kernel-package, and headers....

---

### Post by amohanty on 2005-12-06
Just a bit of advise, when compiling something from source, the only thing you want to do as root is the install part.

1. So download the source to your home dir.
2. unzip it in your home dir
3. cd to the unzipped dir
4. ./configure
5. make
6. sudo checkinstall

HTH

---

### Post by adduds on 2005-12-06
hmmm i put the unzipped part in /etc/alsa

maybe that's the problem

---

### Post by amohanty on 2005-12-06
> adduds@adtop:/etc/alsa/alsa-driver-1.0.10$ ./configure
./configure: line 88: conf16546.sh: Permission denied
./configure: line 89: conf16546.sh: Permission denied

this definitely is the result of putting the source folder in /etc

if you install the packages I mentioned in the above post you should be able to run ./configure without any problems.

---

### Post by adduds on 2005-12-06
i think i need to change the permissions....

```
adduds@adtop:~/pack/alsa-driver-1.0.10$ ./configure
./configure: line 88: conf17644.sh: Permission denied
./configure: line 89: conf17644.sh: Permission denied
**chmod:** cannot access `conf17644.sh': No such file or directory
./configure: line 201: conf17644.file: Permission denied
./configure: line 943: config.log: Permission denied

```

i bolded chmod isn't that how you change file rw permissions?

i re-d/led the alsa-driver-1.0.10.tar.bz2 in /home/adduds/packs

sudo tar xvjpf alsa-driver-1.0.10.tar.bz2

cd.../packs/alsa-driver...

./configure

and get the above still....

---

### Post by amohanty on 2005-12-06
```
sudo chown -R adduds:adduds ~/packs
sudo chmod -R 775 ~/packs
```

should do it.

---

### Post by adduds on 2005-12-06
ok that let me compile w/o using sudo ./configure but now i get

```
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

```

again at the end this is pissing me off I don't neeed the latest drivers, but it would be nice, like wtf, I DON'T UNDERSTAND

EDIT: btw thank you for all of you help

---

### Post by amohanty on 2005-12-06
OK some things to know before you compile from source (I apologize if you already know, consider it a refresher then):

```
./configure
```
essentially checks to see if all the libraries and other resources are available to build the desired package and configure any compile options based on that.

```
make
```
actually compiles all the stuff

```
make install
```
copies all the relevant files and libraries to the right location for the binary to work.

Now when you compile a C/C++ application, it requires certain *.h files and *.lib (static libs) and *.so (shared libs) to get the needed method/function definitions and functionality.

The linux-kernel-headers pacakge should provide the required headers for your file to compile. However sometimes based on the distro the headers might be at a different location.

Try:
```
sudo updatedb
locate -e version.h
```

If it is not in: /usr/src/linux/include/linux
then create a link for it there.

For e.g. if you find that version.h is in :

/usr/include/i386/<kernel version number> (I just made that up)

then you need create link for it like so:

```
sudo ln -s /usr/include/i386/<kernel version number> /usr/src/linux/include
```

HTH

---

### Post by adduds on 2005-12-06
```
adduds@adtop:~$ locate version.h
/usr/include/irssi/irssi-version.h
/usr/lib/perl5/Gnome2/Canvas/Install/gnomecanvasperl-version.h
/usr/lib/perl5/Gnome2/VFS/Install/vfs2perl-version.h

```

That is what it says, theirs not single file that just says version.h, is it irssi-version.h?

---

### Post by amohanty on 2005-12-06
try installing the kernel src

I think you would need to do:

```
sudo apt-get install linux-tree
```

In synaptic look for tree.

AM

---

### Post by adduds on 2005-12-06
k i did that, now what? tried the ./configure still won't go?

---

### Post by dominik_ap on 2008-01-21
Hey i had the same problem, here [http://ubuntuforums.org/archive/index.php/t-355634.html](http://ubuntuforums.org/archive/index.php/t-355634.html) i found this:

sudo apt-get install linux-headers-`uname -r`

it helped me and now i can install it


Dominik F.

---

