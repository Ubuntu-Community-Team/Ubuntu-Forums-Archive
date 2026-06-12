---
title: "Extract, make and install drivers"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by rosco99 on 2007-07-01
I downloaded a driver file and placed it on my home/rosco99 directory.
Instructions to install are as follows:
in a terminal
#cd <directory of source>
# tar -zxf sierra.v.X.Y.Z
cd sierra.v.X.Y.Z

This did not work ---error not a directory.

So I right clicked on the mouse and chose extract to: sierra and I got a file that had 3 files in it.
Makefile, Sierra.c and one other empty file.

I then tried to instal the driver using these instructions
# sudo cd /sierra directory
#make
#make install

I was already in the /home/rosco99 directory so I 
did #make --and received 
make -C/lib/modules/2.6.18.2-34-default/build SUBDIRS=home/rosco99 modules
make[1]: Entering directory '/usr/src/linux-2.6.18.2-34-obj/i386/defaultt'
make[1]: ***No rule to make target 'modules'. Stop.
make [1]: Leaving directory 'usr/src/linux-2.6.18.2-34-obj/i386/default'
make:[default] Error 2

when i did make install I got
install:cannot stat 'sierra.ko': No such file or directory
make: 'install' is up to date.

I am using KDE whereas the original instructions were for Gnome.

Advice gratefully accepted.

---

### Post by Maxtorm on 2007-07-03
According to the following post, it looks as though you need to modify the Makefile:
[http://ubuntuforums.org/showthread.php?t=132477](http://ubuntuforums.org/showthread.php?t=132477)

---

### Post by rosco99 on 2007-07-03
Thanks for that. I have pulled the rest of my hair out. Got exact same error on both kubuntu and Suse 10.2.
Will try to upgrade the makefile.

---

### Post by rosco99 on 2007-07-04
It seems I need the Build-essentials. How do I go about that?

---

### Post by Maxtorm on 2007-07-05
From the terminal:
```
sudo apt-get install build-essential
```

---

