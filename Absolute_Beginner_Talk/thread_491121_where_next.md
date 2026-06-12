---
title: "where next?"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-07-03
I have installed dvdshrink via synaptic, what do I do next and where will I find the program?
Many thanks

benbow@benbow-desktop:~$ tar -xzvf /home/benbow/Downloads/dvdshrink-2.6.1-10mdk.tar.gz
./dvdshrink/
./dvdshrink/usr/
./dvdshrink/usr/bin/
./dvdshrink/usr/bin/batchrip.sh
./dvdshrink/usr/bin/xdvdshrink.pl
./dvdshrink/usr/bin/dvdsfunctions
./dvdshrink/usr/bin/dvdshrink
./dvdshrink/usr/share/
./dvdshrink/usr/share/doc/
./dvdshrink/usr/share/doc/dvdshrink/
./dvdshrink/usr/share/doc/dvdshrink/example.xml
./dvdshrink/usr/share/doc/dvdshrink/batchrip.txt
./dvdshrink/usr/share/doc/dvdshrink/README.txt
./dvdshrink/usr/share/doc/dvdshrink/gpl.txt
./dvdshrink/usr/share/doc/dvdshrink/INSTALL
./dvdshrink/usr/share/icons/
./dvdshrink/usr/share/icons/dvdshrink.xpm
./dvdshrink/usr/share/icons/batchrip.xpm
./dvdshrink/usr/share/applications/
./dvdshrink/usr/share/applications/dvdshrink/
./dvdshrink/usr/share/applications/dvdshrink/32x32/
./dvdshrink/usr/share/applications/dvdshrink/32x32/dvdsrhink.xpm
./dvdshrink/usr/share/applications/dvdshrink/64x64/
./dvdshrink/usr/share/applications/dvdshrink/64x64/dvdshrink.xpm
./dvdshrink/usr/share/applications/dvdshrink/menus/
./dvdshrink/usr/share/applications/dvdshrink/menus/pselect2.mpg
./dvdshrink/usr/share/applications/dvdshrink/menus/pselect3.mpg
./dvdshrink/usr/share/applications/dvdshrink/menus/pselect4.mpg
./dvdshrink/usr/share/applications/dvdshrink/menus/pselect5.mpg
./dvdshrink/usr/share/applications/dvdshrink/menus/pselect6.mpg
./dvdshrink/usr/share/applications/dvdshrink/menus/pselect7.mpg
./dvdshrink/usr/share/applications/dvdshrink/menus/pselect8.mpg
./dvdshrink/usr/share/applications/dvdshrink/menus/nselect2.mpg
./dvdshrink/usr/share/applications/dvdshrink/menus/nselect3.mpg
./dvdshrink/usr/share/applications/dvdshrink/menus/nselect4.mpg
./dvdshrink/usr/share/applications/dvdshrink/menus/nselect5.mpg
./dvdshrink/usr/share/applications/dvdshrink/menus/nselect6.mpg
./dvdshrink/usr/share/applications/dvdshrink/menus/nselect7.mpg
./dvdshrink/usr/share/applications/dvdshrink/menus/nselect8.mpg
./dvdshrink/usr/share/applications/dvdshrink/xdvdshrink_logo.png
./dvdshrink/install.sh
benbow@benbow-desktop:~$

---

### Post by mikewhatever on 2007-07-03
It looks more like compiling from source, by never mind.
Try Alt+F2 -> dvdshrink, or 'locate dvdshrink' in the terminal.

---

### Post by cogadh on 2007-07-03
It looks like you haven't installed it via Synaptic, that looks like you just unpacked a tar ball (like a .zip file). The very last item you list "./dvdshrink/install.sh" is an install script, you'll need to run that from a terminal:
```
cd /home/benbow/Downloads/dvdshrink
sh install.sh
```
If the install script complains about permission or that it can't access certain files, do this instead:
```
sudo sh install.sh
```

---

### Post by Benbow on 2007-07-03
Had to cut the grass in between showers (Brittany). No luck here :
I have tried all three suggestions.
It appears in my home folder as :
/home/benbow/Downloads/dvdshrink-2.6.1-10mdk.tar.gz
1)
benbow@benbow-desktop:~$ cd /home/benbow/Downloads/dvdshrink
bash: cd: /home/benbow/Downloads/dvdshrink: No such file or directory
benbow@benbow-desktop:~$ sh install.sh
sh: Can't open install.sh
2)
benbow@benbow-desktop:~$ locate dvdshrink
/usr/share/automatix2/conf/dvdshrink.desktop
/usr/share/automatix2_bleeder/conf/dvdshrink.desktop
3)
benbow@benbow-desktop:~$ sudo sh install.sh
Password:
sh: Can't open install.sh
benbow@benbow-desktop:~$

---

### Post by Cypher on 2007-07-03
Do
```

cd ~/dvdshrink
sudo sh install.sh

```

---

### Post by Benbow on 2007-07-03
Tried those in various ways. The result is not promising.:
benbow@benbow-desktop:~$ /home/benbow/Downloads/dvdshrink-2.6.1-10mdk.tar.gz
bash: /home/benbow/Downloads/dvdshrink-2.6.1-10mdk.tar.gz: Permission denied
benbow@benbow-desktop:~$ cd ~/dvdsrhink
bash: cd: /home/benbow/dvdsrhink: No such file or directory
benbow@benbow-desktop:~$ sudo sh install.sh
Password:
sh: Can't open install.sh
benbow@benbow-desktop:~$ sudo sh install.sh

---

### Post by bodhi.zazen on 2007-07-03
It looks like the directory you need is :

~/Downloads/dvdshrink

Ans to run :

```
~/Downloads/dvdshrink/usr/bin/dvdshrink
```

Now you can : ```
sudo ln -s ~/Downloads/dvdshrink/usr/bin/dvdshrink /usr/bin/dvdshrink
```

Then to run just enter "dvdshrink" in a terminal without the quotes. You can also make a custom launcher in your menu ;)

Also you may want to check out k9copy:

[http://packages.ubuntu.com/feisty/kde/k9copy](http://packages.ubuntu.com/feisty/kde/k9copy)

> k9copy is a tabbed tool that allows to copy of one or more titles from a DVD9 to a DVD5, in the same way than DVDShrink for Microsoft Windows (R).

---

### Post by Bachstelze on 2007-07-03
There's an install script, why not use it ?

```
cd /home/benbow/Downloads/dvdshrink
sudo ./install.sh
```

---

### Post by Benbow on 2007-07-03
I tried this:

benbow@benbow-desktop:~$ /home/benbow/Downloads/dvdshrink-2.6.1-10mdk.tar.gz
bash: /home/benbow/Downloads/dvdshrink-2.6.1-10mdk.tar.gz: Permission denied
benbow@benbow-desktop:~$ cd ~/dvdsrhink
bash: cd: /home/benbow/dvdsrhink: No such file or directory
benbow@benbow-desktop:~$ sudo sh install.sh
Password:
sh: Can't open install.sh
benbow@benbow-desktop:~$ ~/Downloads/dvdshrink/usr/bin/dvdshrink
/home/benbow/Downloads/dvdshrink/usr/bin

And got this:
________________________________________________________

   DVDShrink 2.6.1 - May 04, 2007
   Rick Saunders (ozzzy1@gmail.com)
________________________________________________________

   Required tools in package 'subtitleripper' missing or unexecutable!

   You are missing needed tools or the tools are not executable
   by your user. Update or repair your toolset as needed.

and then I tried this:
benbow@benbow-desktop:~$ sudo ln -s ~/Downloads/dvdshrink/usr/bin/dvdshrink /usr/bin/dvdshrink
Password:
benbow@benbow-desktop:~$ clocks
bash: clocks: command not found
benbow@benbow-desktop:~$ sudo ln -s ~/Downloads/dvdshrink/usr/bin/dvdshrink /usr/bin/dvdshrink
ln: creating symbolic link `/usr/bin/dvdshrink' to `/home/benbow/Downloads/dvdshrink/usr/bin/dvdshrink': File exists
benbow@benbow-desktop:~$ 

Did I ought to consider redoing the whole thing from scratch. I seem to have made a bit of a mess of it so far!

---

### Post by Bachstelze on 2007-07-03
See last message...

---

### Post by Benbow on 2007-07-03
Thanks........I then got this but am uncertain how to proceed with the missing bits?
benbow@benbow-desktop:~/Downloads/dvdshrink$ sudo ./install.sh


DVDShrink installer v1.1

Checking for dependencies
   SubtitleRipper not installed or utilities not executable
   GOcr is not installed or utilities not executable

   One or more of the utilities that DVDShrink requires are not installed or
   are not executable. Continue the installation? (y/n)

---

### Post by Bachstelze on 2007-07-03
I think that speaks for itself. Some of the other software requires by DVDShrink are not installed on your system. You can either install them and then start the DVDShrink installer again or install DVDShrink nevertheless. But of course, if you don't install them, you won't be able to use the functionality they provide.

---

### Post by orb9220 on 2007-07-03
Or do it the easy way.
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)
[https://help.ubuntu.com/community/DVDShrink](https://help.ubuntu.com/community/DVDShrink)

These are for the window version of DVDshrink and DVDecrypter which I use mainly because the Linux versions of ripping programs comes no where near the functionality and features that these two give me.

Sorry but k9copy,k3b,etc.. are just not there yet and I have tried them all. I hope this will change but for doing Video Editing,Graphics editing I still need to dual boot. I hope this will change and we end up with some powerful tools for doing video,graphics.

---

