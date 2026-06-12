---
title: "Installing standard source package?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Pandemic187 on 2007-05-16
Hello all.

Amongst the many, many guides for Linux, I have not been able to find any explaining each step of the standard procedure for installing source packages. I know one must use the "./configure" and "make" commands, but I'm still confused. First of all, am I wrong, or should the folder be placed somewhere other than the desktop before it is installed? I mean I was thinking it should be placed in usr/lib, but of course root privileges are needed to do this. So, can programs be installed from the desktop, or must the folder be placed in another directory?

If someone could explain this basic procedure to me, that would be nice!

---

### Post by FuturePast on 2007-05-16
You need root privileges to install apps to the standard locations. 
If you do not have root then you can specify a different install location to the configure script e.g.
$ ./configure --prefix=~/opt/<app-name> ; make; make install



It doesn't matter at all where the source package file is placed.

---

### Post by jputman01 on 2007-05-16
i normally move mine to /usr/lib or /opt or wherever i want them to avoid a cluttered desktop, you can move them via terminal with the command

```
sudo mv nameoffile /directory/youwant
```

then install from there

---

### Post by taurus on 2007-05-16
Section 4.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Pandemic187 on 2007-05-16
```

bob@BobsLaptop:~/Desktop$ dir
**avant-window-navigator-0.1.1   **        jre1.6.0_01
avant-window-navigator-0.1.1-2.tar.gz  OSX3.3.tar.gz
DreamAccurateTiger.emerald             OSX-theme
Fonts.zip                              OSX-theme.tar.gz
gtk-osx-theme.tar.gz                   osx-top-bar-1440x900.png
bob@BobsLaptop:~/Desktop$ sudo mv avant-window-navigator-0.1.1 usr/lib
mv: cannot move `avant-window-navigator-0.1.1' to `usr/lib': No such file or directory

```

Okay, how does that make sense?

---

### Post by FuturePast on 2007-05-16
Please tell us what you are trying to do. 

usr/lib is very different to /usr/lib

---

### Post by Pandemic187 on 2007-05-16
I'm just trying to move this folder from my desktop to the lib folder within usr...

---

### Post by jputman01 on 2007-05-16
> **Pandemic187 said:**
> I'm just trying to move this folder from my desktop to the lib folder within usr...


use ```
sudo mv filename /usr/lib
```

---

### Post by FuturePast on 2007-05-16
Why don't you do?
$ sudo make install

---

### Post by Pandemic187 on 2007-05-16
Uhh sure. Right after I understand what this means...

```

bob@BobsLaptop:~/Desktop/avant-window-navigator-0.1.1$ make
make: *** No targets specified and no makefile found.  Stop.
bob@BobsLaptop:~/Desktop/avant-window-navigator-0.1.1$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
bob@BobsLaptop:~/Desktop/avant-window-navigator-0.1.1$ 

```

---

### Post by jputman01 on 2007-05-16
> **Pandemic187 said:**
> Uhh sure. Right after I understand what this means...

```

bob@BobsLaptop:~/Desktop/avant-window-navigator-0.1.1$ make
make: *** No targets specified and no makefile found.  Stop.
bob@BobsLaptop:~/Desktop/avant-window-navigator-0.1.1$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
bob@BobsLaptop:~/Desktop/avant-window-navigator-0.1.1$ 

```

did you run ```
./configure
``` first before running ```
make
```

---

### Post by Pandemic187 on 2007-05-16
To jputman: Yes. Yes I did.

---

### Post by jputman01 on 2007-05-16
> **Pandemic187 said:**
> Uhh sure. Right after I understand what this means...

```

bob@BobsLaptop:~/Desktop/avant-window-navigator-0.1.1$ make
make: *** No targets specified and no makefile found.  Stop.
bob@BobsLaptop:~/Desktop/avant-window-navigator-0.1.1$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.
bob@BobsLaptop:~/Desktop/avant-window-navigator-0.1.1$ 

```

this looks like you are still in the Desktop, did you move it to /usr/lib/avant*? if so go there and run your commands

did you get any errors during ./configure before??

have you installed ```
build-essential autotools-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf subversion gnome-common
```

---

### Post by Pandemic187 on 2007-05-16
> **jputman01 said:**
> this looks like you are still in the Desktop, did you move it to /usr/lib/avant*? if so go there and run your commands

did you get any errors during ./configure before??


Please see post #5. No, I did not get any errors before ./configure. I'll check on those packages though.

---

### Post by jputman01 on 2007-05-16
> **Pandemic187 said:**
> ```

bob@BobsLaptop:~/Desktop$ dir
**avant-window-navigator-0.1.1   **        jre1.6.0_01
avant-window-navigator-0.1.1-2.tar.gz  OSX3.3.tar.gz
DreamAccurateTiger.emerald             OSX-theme
Fonts.zip                              OSX-theme.tar.gz
gtk-osx-theme.tar.gz                   osx-top-bar-1440x900.png
bob@BobsLaptop:~/Desktop$ sudo mv avant-window-navigator-0.1.1 usr/lib
mv: cannot move `avant-window-navigator-0.1.1' to `usr/lib': No such file or directory

```

Okay, how does that make sense?

what are you wanting me to look at? first it shows you are in the desktop directory second it says it could not be moved, which i already addressed it is because you need to use /usr/lib instead of usr/lib

also are you using feisty, if so awn is in the repos

---

### Post by Pandemic187 on 2007-05-16
Okay, so you were right about the usr/lib thing.

And I didn't know awn was in the repos! Grr. I searched for it though, and I didn't see anything. Is the package actually called awn, or is it something else? And yes, I have all the repositories checked in settings.

---

### Post by jputman01 on 2007-05-16
here you go, here is a how to i found

[http://ubuntuforums.org/showthread.php?t=385981&highlight=awn]("http://ubuntuforums.org/showthread.php?t=385981&highlight=awn")

you will need to add some sources to your repos, the instructions are pretty straight forward, feel free to PM me if you have any trouble and ill see if i can help, i havent installed awn myself but thought i would try to help you out

one thing from this how to that i notice right of the bat is that it says to use ./autogen.sh instead of ./configure, but you may want to just start fresh with the how to

---

### Post by SteveHoffmanUK on 2007-05-16
If you're looking for a good plain English guide to installing anything in Ubuntu, I suggest you have a look at:
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by FuturePast on 2007-05-16
Look, whatever happens, you don't need to move the directory to /usr/lib. It's completely unnecessary.

---

