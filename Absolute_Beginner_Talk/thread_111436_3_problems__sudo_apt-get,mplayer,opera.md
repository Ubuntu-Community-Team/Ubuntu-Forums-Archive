---
title: "3 problems : sudo apt-get,mplayer,opera"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by Mis_Uszatek on 2006-01-02
Hello

First:
I have been trying to installl opera on Ubuntu

I have downloaded 
opera_8.51-20051114.6-shared-qt_en_etch_i386.deb
from opera homepage
and tried to install it by command

$ sudo apt-get install opera_8.51-20051114.6-shared-qt_en_etch_i386

all I get is :
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package opera_8.51-20051114.6-shared-qt_en_etch_i386

I was trying different combinations, like full path :

$ sudo apt-get install /home/user_name/Desktop/opera_8.51-20051114.6-shared-qt_en_etch_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package

and package is there for sure

user_name@ip:~/Desktop$ ls
opera_8.51-20051114.6-shared-qt_en_etch_i386.deb



Second problem :
administration->addapplication

I am trying to install mplayer, and all I got is :
"Application 'mplayer' not available
The application can not be found in your archive. This usually means that it is not available for your hardware plattform."

Third :
Is it possible to play *avi, *mpg, *wmv files by TotemMoviePlayer

Everying what I have got is :
"There were no decoders found to handle the stream, you might need to install the corresponding plugins"


Thanks for help.

---

### Post by Clazzy on 2006-01-02
You need to use sudo dpkg -i opera_8.51-20051114.6-shared-qt_en_etch_i386.deb for it to work.
apt-get is used to download from the repositories, not for installing specific .deb files.

For mplayer, I believe you need to uncomment the multiverse repositories in your /etc/apt/sources.list
After you've done that, sudo apt-get update and then sudo apt-get install mplayer

Hope that helps.

---

### Post by Mis_Uszatek on 2006-01-03
Yes, dpgk helped, I have installed it.

As for mplayer, i have to switch into advanced mode of synaptic, and then choose mplayer for x586, it was trying to install dummy mplayer for x686 by default.

Thanks very much.

---

### Post by Mustard on 2006-01-03
Check this guide out for setting up totem to play movies and music...
[http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/ch03.html#sect-music-and-movies)

Make sure you visit the link given on the page for instructions on installing w32codecs.

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Madpilot on 2006-01-03
And for Opera in Ubuntu:
[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

---

