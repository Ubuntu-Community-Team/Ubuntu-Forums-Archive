---
title: "sudo apt-get permission?!?"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by Mosey on 2005-10-08
When I'm using console to attempt to install some plugins the good old "su>password" command dosn't seem to work...(recently switched from Debian) and when I try to just install I get this:

admin@ubuntu:~$ $sudo apt-get install w32plugins
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

How do I get permission to install packages...?

---

### Post by Pablo_Escobar on 2005-10-08
1. Try : sudo apt-get install w32plugins instead of **$**sudo apt-get install w32plugins

2. Is Your Synaptic running, if yes, turn it off when using apt-get

---

### Post by ubuntu_demon on 2005-10-08
I think you mean w32codecs instead of w32plugins. The best source for w32codecs in hoary right now (AFAIK) is :

```

deb ftp://cipherfunk.org/pub/packages/ubuntu/ hoary main

```

you have to add that line in your sources.list

Most users also want acces to universe and multiverse. Add "universe multiverse" at the end of each line which starts with "deb" and contains "main" except for the new line / repo I just gave.

you can edit your sources.list by :
$ sudo pico /etc/apt/sources.list (without the $)
or graphically by :
$ sudo gedit /etc/apt/sources.list 

after editting the sources.list do these commands :

$sudo apt-get update
$sudo apt-get upgrade
$sudo apt-get install w32codecs

to help you start with ubuntu go here :
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

