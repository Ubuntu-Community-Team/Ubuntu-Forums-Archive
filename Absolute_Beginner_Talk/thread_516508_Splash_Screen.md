---
title: "Splash Screen"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by goTUX! on 2007-08-03
I have always used gnome, but decided to use kde for one session...now when i start up instead of the UBUNTU splash screen i get KUBUNTU instead...is there any way to get that back to the normal UBUNTU screen on startup?

---

### Post by S15_88 on 2007-08-03
i'm not 100% about getting ubuntu back, but i believe you could. there is a file  /boot/grub/menu.lst in that file you can remove the words quite and splash and that will show the boot process so i guess somewhere in the file it should specify KDE or Ubuntu and make sure that quiet and splash are NOT commented or have NOT been removed.  hope that helps!

Thanks, Alain

---

### Post by testube_babies on 2007-08-03
Well, here's how to build a program that will let you choose your usplash theme:

1) Get all of the dependencies (for systems older than Feisty use usplash-dev instead of libusplash-dev):
```
sudo apt-get install build-essential libusplash-dev libgtk2.0-dev
```

2) Grab the usplash-switcher.c source code from [http://web.archive.org/web/20070314035305/www.kaarsemaker.net/files/Software/usplash-switcher.c](http://web.archive.org/web/20070314035305/www.kaarsemaker.net/files/Software/usplash-switcher.c)

3) Create a new file in the same directory as usplash-switcher.c and name it Makefile with the following contents:
```
CC=gcc
CFLAGS=$(shell pkg-config --cflags gtk+-2.0) -rdynamic -g
LIBS=$(shell pkg-config --libs gtk+-2.0) -ldl

usplash-switcher: usplash-switcher.c
	$(CC) -o $@ $< $(CFLAGS) $(LIBS)
```

4) In the source directory,
```
make usplash-switcher
```


When it's finished, you should be left with a usplash-switcher executable file.  You can delete the source file and Makefile.

---

### Post by ATOMICplayer on 2007-08-03
So this will give you options at the login to choose your session (KDE, gnome, XGL, etc.) ?

---

### Post by testube_babies on 2007-08-03
Upon further research, it seems that the version of usplash in Dapper might be too old to use usplash-switcher.  So, here are some new methods:

Method 1:  see if you can select the Ubuntu usplash using
```
sudo update-alternatives --config usplash-artwork.so
```

Method 2:  reinstall usplash
```
sudo apt-get remove kubuntu-artwork-usplash
sudo apt-get install --reinstall usplash
```

After either of these, you will have to regenerate the initramfs:
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

### Post by testube_babies on 2007-08-03
> **ATOMICplayer said:**
> So this will give you options at the login to choose your session (KDE, gnome, XGL, etc.) ?

No, this lets you choose the boot splash screen (ie the Ubuntu logo with the loading bar when you first start up your computer).  To install different "sessions" see here:
[http://psychocats.net/ubuntu/xubuntu](http://psychocats.net/ubuntu/xubuntu)
[http://psychocats.net/ubuntu/gnome](http://psychocats.net/ubuntu/gnome)
[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

---

### Post by ATOMICplayer on 2007-08-03
> **testube_babies said:**
> No, this lets you choose the boot splash screen (ie the Ubuntu logo with the loading bar when you first start up your computer).  To install different "sessions" see here:
[http://psychocats.net/ubuntu/xubuntu](http://psychocats.net/ubuntu/xubuntu)
[http://psychocats.net/ubuntu/gnome](http://psychocats.net/ubuntu/gnome)
[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

Thanks!

---

### Post by johntkucz on 2007-08-03
> **testube_babies said:**
> Well, here's how to build a program that will let you choose your usplash theme:

1) Get all of the dependencies (for systems older than Feisty use usplash-dev instead of libusplash-dev):
```
sudo apt-get install build-essential libusplash-dev libgtk2.0-dev
```

2) Grab the usplash-switcher.c source code from [http://web.archive.org/web/20070314035305/www.kaarsemaker.net/files/Software/usplash-switcher.c](http://web.archive.org/web/20070314035305/www.kaarsemaker.net/files/Software/usplash-switcher.c)

3) Create a new file in the same directory as usplash-switcher.c and name it Makefile with the following contents:
```
CC=gcc
CFLAGS=$(shell pkg-config --cflags gtk+-2.0) -rdynamic -g
LIBS=$(shell pkg-config --libs gtk+-2.0) -ldl

usplash-switcher: usplash-switcher.c
	$(CC) -o $@ $< $(CFLAGS) $(LIBS)
```

4) In the source directory,
```
make usplash-switcher
```


When it's finished, you should be left with a usplash-switcher executable file.  You can delete the source file and Makefile.


That's a ridiculous solution.  The work to needed to put into that program is far greater than just doing it by hand via menu.lst alterations.  Occam's razor.  changing the menu.lst is easier, simpler and faster, than installing all of that extra junk.  

Here's multiple links on it:

[http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)
[http://ubuntu.wordpress.com/2006/03/21/add-a-grub-splash-image/](http://ubuntu.wordpress.com/2006/03/21/add-a-grub-splash-image/)
[http://ubuntuforums.org/showthread.php?p=3129816#post3129816](http://ubuntuforums.org/showthread.php?p=3129816#post3129816)

I also tweaked the menu colors if you're interested:
[http://ubuntuforums.org/showthread.php?t=514477](http://ubuntuforums.org/showthread.php?t=514477)

Not sure if that hits it.

---

### Post by testube_babies on 2007-08-03
> **johntkucz said:**
> Here's multiple links on it:

[http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)
[http://ubuntu.wordpress.com/2006/03/21/add-a-grub-splash-image/](http://ubuntu.wordpress.com/2006/03/21/add-a-grub-splash-image/)
[http://ubuntuforums.org/showthread.php?p=3129816#post3129816](http://ubuntuforums.org/showthread.php?p=3129816#post3129816)

I also tweaked the menu colors if you're interested:
[http://ubuntuforums.org/showthread.php?t=514477](http://ubuntuforums.org/showthread.php?t=514477)

Not sure if that hits it.

Those are for GRUB splash images, which have nothing to do with the actual Kubuntu/Ubuntu loading screen (usplash).  Usplash is notoriously difficult to customize, and usplash-switcher is a tiny executable file that makes it possible to switch themes with a single click.

---

