---
title: "Terminal commands"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by chesman on 2006-12-30
Okay,
i am now using Ubuntu, installed and all, and i am loving it. But alas, i am not very good with the terminal yet.


I am trying to install my ATI driver from the website, but they recommended running a file from the terminal first to find out what version of XFree86 i am running.

So i downloaded the file check.sh, and i can navigate in terminal so i can see the file when i do a List on the dir, but i am unsure on how to run that file :(


help would be wonderful

Chesman

---

### Post by maxamillion on 2006-12-30
You aren't running Xfree. Ubuntu uses Xorg. 

To run that file, enter the commands at the command line in the directory of the file
```
chmod +x check.sh
sh check.sh
```

---

### Post by Hossie on 2006-12-30
```
chmod +x check.sh
```

This makes the file *executable*.

```
sudo ./check.sh
```

This runs the script as root.

€: Too late. :(

---

### Post by chesman on 2006-12-30
Thanks guys, and thanks Hossie for explaining what those commands were doing

 :)

cheers

---

### Post by chesman on 2006-12-30
Okay, i ran those comands and i got this error:

> =====================================================================
 ATI Technologies 
=====================================================================
You are either not running this script from the console
or simply do not have console ownership.  Requirement failed.
Unable to determine XFree86 Version. Stopping now.

---

### Post by chesman on 2006-12-30
and i just realized that ATI has an xorg version... :( lol


guess ill DL that and install

---

### Post by Hossie on 2006-12-30
I dont know what script this is and what it should do, but it won't find XFree86, because Ubuntu does not use it. If it can also detect Xorg, you may try running the script as root. Maybe they mean by "running in console" on a real console? Try hitting Ctrl+Alt+F1 (but I don't think that is what they mean).

&#8364;: And again, too late. :(

---

### Post by chesman on 2006-12-30
Okay, i tried running that file (X.org 6.8 Drivers) and i ge the following error :(

> Could not open "fglrx_6_8_0-8.32.5-1.i386.rpm"

Archive type not supported.

---

### Post by Hossie on 2006-12-30
You could "alien" that file so that it is in the debian-format, but I think there are better ways for installing the ATI drivers. Did you check the wiki? I use Nvidia cards, so I can't really help you.

&#8364;: Ah, this time I am not too late. \o/

---

### Post by chesman on 2006-12-30
nope, no you are not :) uill check the wiki, keep forgetting everything, ir ead that it is available in the respositories as well, but i cant find how to turn them on.. :(

man

---

### Post by maxamillion on 2006-12-30
.rpm is the package file format that RedHat and its derived distributions of linux run, you will need a .deb for ubuntu because it is the debian package format but you can change the .rpm to a .deb using the "alien" tool, I am not sure if it is installed by default on ubuntu. I know it is not on xubuntu so you will first need to open a terminal and type this 

```
sudo aptitude install alien
```

it will either download and install or tell you it is already installed ant then you can do this

```
sudo alien -d fglrx_6_8_0-8.32.5-1.i386.rpm
```

and that should generate a file called "fglrx_6_8_0-8.32.5-1.i386.deb"

from there do:

```
sudo dpkg -i fglrx_6_8_0-8.32.5-1.i386.deb
```

you should be good to go from there

---

### Post by chesman on 2006-12-30
Tried the first command and got this..

> ches@belix:/home$ cd..
bash: cd..: command not found
ches@belix:/home$ cd /
ches@belix:/$ sudo aptitude install alien
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

