---
title: "Installing Plugins"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by kokomonjo on 2007-12-20
Hi All!

I am new to Ubuntu and Linux. I just installed Ubuntu 7.10 amd64. I would like to know how to install a plugin i just downloaded in .tar.gz file.

---

### Post by PeterJS on 2007-12-20
Well... that depends, What program is the plugin a program for? Tar.gz is just an archive file, like a zip.

---

### Post by kokomonjo on 2007-12-20
It is a wallpaper plugin for compiz.

---

### Post by guy33 on 2007-12-20
I need to know how to install a new plug in for a flash player tar.gz
:confused:

---

### Post by kokomonjo on 2007-12-20
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

Here is a link that will tell you how to install a flashplayer plugin

---

### Post by PeterJS on 2007-12-20
After looking around, I couldn't find any prebuilt copies of the module for ubuntu. So it looks like you're going to have to build it yourself. First you're going to want to install the build tools. Open up a terminal and install them with:
```

sudo apt-get install build-essential checkinstall

```Then unpack the archive some where, pick anywhere doesn't really matter you're going to delete that folder when you're done. Then open up a terminal and change to the directory to where you unpacked the tar ball. First run:
```

./configure

```Odds are this will produce errors and complain about libraries not being installed, this step never goes well the first time. But since I don't know which libraries it wants, I can't offer specifics as to how to fix it, yet. We'll deal with this as it comes.
Then:
```

make

```This is going take a while go get some coffee. Hopefully this step won't fail. In looking around it looks like it's kinda hit or miss which version of the plugin work with which versions of Compiz, hopefully you got a good one.
Then lastly:
```

sudo checkinstall

```Configure and enjoy.

---

### Post by kokomonjo on 2007-12-21
Thanks for all your help. I got the tar from gitweb if that helps any. 

Ok so i did the first line of code that you gave me in terminal. But i got confused on the second part. This is what i did I unpacked the tar file to my desktop and in terminal entered in the location of the unpackaged folder followed by "./configure" code. Is this correct? When i pressed enter It said no such file directory. Next i entered "make" and it said no target specified. So what have i done wrong? I didnt bother with the check install command.

---

### Post by PeterJS on 2007-12-21
The configure step is supposed to set up the targets for the make step. I tried looking around on git-web and couldn't find a link to the tar ball, could you post that here. I'd like to take a look at what's in the package, there should be a configure file... but somethings use other build systems.

---

### Post by kokomonjo on 2007-12-21
[http://gitweb.opencompositing.org/?p=fusion/plugins/wallpaper;a=summary](http://gitweb.opencompositing.org/?p=fusion/plugins/wallpaper;a=summary)

here is the page. I just grabbed the first one dated october 10, 2007 the snapshot is the tarball

---

### Post by PeterJS on 2007-12-21
> **kokomonjo said:**
> [http://gitweb.opencompositing.org/?p=fusion/plugins/wallpaper;a=summary](http://gitweb.opencompositing.org/?p=fusion/plugins/wallpaper;a=summary)

here is the page. I just grabbed the first one dated october 10, 2007 the snapshot is the tarball


In retrospect that seem rather obvious. I grabbed it, and tried to build it, but it never built. Just as a point of reference here's what I did:
```

peter@Osirus:~$ cd Desktop/wallpaper/
peter@Osirus:~/Desktop/wallpaper$ ls
DOCUMENTATION  Makefile  plugin.info  wallpaper.c  wallpaper.xml.in
peter@Osirus:~/Desktop/wallpaper$ make
convert   : wallpaper.xml.in -> build/wallpaper.xml
bcop'ing  : build/wallpaper.xml -> build/wallpaper_options.h/bin/sh: --header=build/wallpaper_options.h: not found
make: *** [build/wallpaper_options.h] Error 127

```

There's another thread about it here:
[http://ubuntuforums.org/showthread.php?t=643496](http://ubuntuforums.org/showthread.php?t=643496)
It might be worth taking a look, according to that thread the 2007-08-06 snapshot works, but I couldn't get it to, good luck sorry I can't help.

---

### Post by kokomonjo on 2007-12-21
Thank you for your time! i really appreciate it. Its no problem i sure i will manage to get by in life somehow without it. HA ! just kidding i really do appreciate all your efforts, peterjs

---

