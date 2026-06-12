---
title: "[SOLVED] make new usr directories?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-07-08
Hi all, just been looking around and found this app
> xdesktopwaves
so I downloaded and followed the instructions in the readme file.
Went fine as far as 'make' but then 'make install' gives me an error;
```
ozymandias@ramses:~/xdesktopwaves-1.3$ sudo make install
install -c -m 0755 -s xdesktopwaves /usr/X11R6/bin/xdesktopwaves
install -c -m 0444 xdesktopwaves.1 /usr/X11R6/man/man1/xdesktopwaves.1
install: cannot create regular file `/usr/X11R6/man/man1/xdesktopwaves.1': No such file or directory
make: *** [install] Error 1
```
and yes there is no directory called /usr/X11R6/man/man1
How can I create it? I can't use the normal GUI method, and gedit won't do it. I don't know the terminal commands for this.
I thought this happened automatically with 'make'

---

### Post by dreadlord_chris on 2007-07-08
> **carloslosgrande said:**
> Hi all, just been looking around and found this app

so I downloaded and followed the instructions in the readme file.
Went fine as far as 'make' but then 'make install' gives me an error;
```
ozymandias@ramses:~/xdesktopwaves-1.3$ sudo make install
install -c -m 0755 -s xdesktopwaves /usr/X11R6/bin/xdesktopwaves
install -c -m 0444 xdesktopwaves.1 /usr/X11R6/man/man1/xdesktopwaves.1
install: cannot create regular file `/usr/X11R6/man/man1/xdesktopwaves.1': No such file or directory
make: *** [install] Error 1
```
and yes there is no directory called /usr/X11R6/man/man1
How can I create it? I can't use the normal GUI method, and gedit won't do it. I don't know the terminal commands for this.
I thought this happened automatically with 'make'

```

sudo mkdir /usr/X11R6/man
sudo mkdir /usr/X11R6/man/man1

```
will create the proper directories for you...

---

### Post by carloslosgrande on 2007-07-08
Hi Dreadlord Chris, that was it exactly, thanks man.

---

