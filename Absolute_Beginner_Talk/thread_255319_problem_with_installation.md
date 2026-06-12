---
title: "problem with installation"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Sakura1105 on 2006-09-11
can someone help me? i'm still new in linux world..
when i try to install some software using terminal...
i type ./configure but it came with some errors, so i cant continue to make install...

```
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
[COLOR="Red"]configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.[/COLOR]

```

---

### Post by risbac on 2006-09-11
apt-get install gcc ?

And more generally, did you apt-get install build-essential ?

It should help!

---

### Post by Sakura1105 on 2006-09-11
i still dont get it sorry...
it'll be helpfull if you show me step by step what to do.. :P

---

### Post by monktbd on 2006-09-11
what do you want to install?

there is no need for compiling for most applications.

please read
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
it says all you need also for compiling

---

### Post by Najand on 2006-09-11
You need a c compiler to be able to compile your software... So first you need a compiler... As risbac says, you can install it using apt-get which is a text base package manager. 
Or you can use other package managers like altitude (text base) or Synaptic (With Graphics under Gnome) or Adept (With Gui under KDE)

So let us install it using synaptic....
Click on System on top of the screen.... Then Click Administration....
Then Click on Synaptic Package Manager.
It will ask for your password...
Enter your password... And push Enter.
A new window will open containing all available packages... 
So find "gcc"
Then Right Click on "gcc" and select "Mark for installatin"
Then click on Apply on top of the page. It will install it automatically...
You may need "make" too... So Right Click on "make" and select "Mark for installatin"
Then click on Apply on top of the page.
Close Synaptic... And continue your installation.

---

### Post by Sakura1105 on 2006-09-11
i need to install LongPlayer, a mp3 player...
[http://lplayer.sourceforge.net/](http://lplayer.sourceforge.net/)

or perhaps, u can recommend me what mp3 player is easy to use/install..

---

### Post by monktbd on 2006-09-11
rhythmbox, xmms, totem, banshee, amarok, .....
almost countless :).

---

