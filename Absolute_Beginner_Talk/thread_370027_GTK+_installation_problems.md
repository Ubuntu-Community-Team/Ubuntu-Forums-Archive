---
title: "GTK+ installation problems"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by rula_ on 2007-02-25
hey!
I got ubuntu installed for almost 2 weeks now.
I'm tryin for about 5 days to install GTK+ and I can't get it done.
when I type:
./configure
I'm gettin this error: 
...
checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.12.0    atk >= 1.9.0    pango >= 1.13.0    cairo >= 1.2.0) were not met:

No package 'pango' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

but, I have installed all the dependences as required, probably I did something wrong.
Anyone can help me? please!
thanks!

---

### Post by jvc26 on 2007-02-25
The bit about you missing the dependencies: Have you got the ones of high enough version:
glib-2.0 >= 2.12.0 atk >= 1.9.0 pango >= 1.13.0 cairo >= 1.2.0
i.e. glib2.0 1.12.0 or better, atk 1.9.0 or better, pango 1.13.0 or better etc. These may be later versions than the ones available in the repos.
Il

---

### Post by rula_ on 2007-02-25
thanks man!!
ok, I had those sorted out, now I'm getting this:

checking for GLIB - version >= 2.12.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.12.9, but GLIB (2.12.4)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.12.0 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/pub/gtk/](ftp://ftp.gtk.org/pub/gtk/).

---

### Post by christhemonkey on 2007-02-25
Why are you trying to compile GTK+?
What version of ubuntu are you running?
Is there something wrong with the version in the repositories?

---

### Post by rula_ on 2007-02-25
I'm running the latest version, 6.10
I got some other stuff that require GTK+.. for example I can't do the stunning of the system without it.
I don't know about the repositories.

---

### Post by rula_ on 2007-02-25
I didn't find GTK+ in repositories, can anyone help me??

---

### Post by rula_ on 2007-02-25
up

---

### Post by mcduck on 2007-02-25
If you are running Gnome or XFCE desktop you already have GTK, as they both use it.. There is absolutely no wy to run either of these desktops without GTK :D

---

### Post by rula_ on 2007-02-25
why when I install gnome-hideseek, the package installer says  everythiong is OK, but there is nothing in System Tools?
and I'm getting this when I try to install something else:

checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

---

### Post by christhemonkey on 2007-02-25
If your trying to compile it then you probably need at least:
libgtk2.0-dev and build-essential

also try running gnome-hideseek from a terminal if you have compiled and installed it already correctly.

EDIT: You could also try installing the .rpm packages they have on their website.
```
sudo apt-get install alien 
```
This will install a program that can be used to install packages that are for .rpm based distros.
Use it like this:
```
sudo alien FOO.rpm 
```
This (should) result in a .deb file that can then easily be installed:
```
sudo dpkg -i ./FOO.deb 
```

---

### Post by mcduck on 2007-02-25
So you are you trying to compile the hideseek application? Then what you need is libraries, not the actual working GTK+ :) Most likely the right package would be libgtk2.0-0.

edit: I tried to convert the RPMpackage with alien, it installed fine but segfaulted when I tried to run the app. But there's even better way, just download the .deb package for Ubuntu 6.10 from here: [http://www.getdeb.net/search.php?release=Edgy&keywords=Hide%20and%20Seek]("http://www.getdeb.net/search.php?release=Edgy&keywords=Hide%20and%20Seek")

---

### Post by rula_ on 2007-02-25
when I try to install the libgtk2.0-dev it says that a later version was found, and for build-essential it says that I got the latest version. and when I try to compile something it says the same:

checking for pkg-config... /usr/local/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

why?? if there is GTK on the system?? it probably can't see the right path, how and where can I change that?
I have alien installed but I can't see it in the Main Menu... I can't really use the command line, as I said I  got ubuntu for about 10days.. I can do ./configure, make and make install...

I don't know how to run hideseek from the command line as well... but I found it somewhere else!!! it was in System>Preferencies, not in System Tools, where I was looking for..

---

### Post by christhemonkey on 2007-02-25
Alien is a command line only tool use it like i said (a refresher: )

Download gnome-hideseek-0.6.0-1.i386.rpm from [http://prdownloads.sourceforge.net/hideseek/gnome-hideseek-0.6.0-1.i386.rpm?download](http://prdownloads.sourceforge.net/hideseek/gnome-hideseek-0.6.0-1.i386.rpm?download)
Then type this:
```
cd ~/Desktop #Or wherever you saved the file (firefox defaults to here)
sudo alien ./gnome-hideseek-0.6.0-1.i386.rpm
```

This should then leave you with a gnome-hideseek-0.6.0-1.deb on your desktop that you can just double click and install.

---

### Post by rula_ on 2007-02-25
it's ok now, with hideandseek.. thanks man!
I found that!
but I keep gettin this error when I try to compile something else.

checking for pkg-config... /usr/local/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I don't understand why!??!! how can I show it the right path?

---

### Post by christhemonkey on 2007-02-25
This might be due to how its packaged? Its looking for gtk+-2.0 which doesnt exist as a package on ubuntu.
EDIT: but the package libgtk2.0-dev does supply this dependency so try installing the latest version in the repositories.

What is it your trying to compile?

---

### Post by rula_ on 2007-02-25
I'm tryin to compile aircrack-ng! 
and it wants the gtk+.
I found it with the package manager, and installed it, but there is no icons in the main menu!
how can I run it with the command line?

---

### Post by christhemonkey on 2007-02-25
You have found aircrack-ng or libgtk2.0-dev?

And aircrack-ng is a command line only tool (as far as i can see) so youl need to learn how to use it.
Some tutorials:
[http://www.aircrack-ng.org/doku.php?id=aircrack-ng&DokuWiki=87e3ecc7fa91e7a5d616e7a54c99a428](http://www.aircrack-ng.org/doku.php?id=aircrack-ng&DokuWiki=87e3ecc7fa91e7a5d616e7a54c99a428)
[http://www.tuto-fr.com/en/tutorial/tutorial-crack-wep-aircrack.php](http://www.tuto-fr.com/en/tutorial/tutorial-crack-wep-aircrack.php)
[http://mpf.danslesbois.org/howto-s/open-source/divers/wifi-aircrack-ng](http://mpf.danslesbois.org/howto-s/open-source/divers/wifi-aircrack-ng) (this ones in french)

---

### Post by rula_ on 2007-02-25
yes, I found them in package manager..
thanks man! coz as I see, it seems that you are right, it's a command line tool only.
but it keeps me wonder about the GTK+ error.. something's wrong here anyway!

---

### Post by christhemonkey on 2007-02-25
Found a better ubuntu focused tutorial:
[http://ryanunderdown.com/wp-content/uploads/2007/02/turkeyfarm.html](http://ryanunderdown.com/wp-content/uploads/2007/02/turkeyfarm.html)

And the whole idea of running a distro with prepackaged binaries is that you dont have to compile lots of things from source.

You said that there was an updated version of libgtk2.0-dev? Try installing it.
```
sudo apt-get install libgtk2.0-dev
sudo apt-get upgrade 
```

---

