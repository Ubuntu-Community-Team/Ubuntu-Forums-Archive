---
title: "How to install software on linux"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by dbrewer on 2006-03-05
I have been trying to search for help on exactly how to install new software on linux. It seems like it should be the easiest thing in the world yet I still haven't been able to figure it out. I realize I have to use .deb files and I have been told to use arhive manager but I have yet to successfully install any software. I have tried installing opera on ubuntu and firefox on kubuntu(i have 2 machines running, i couldn't decide which distro I liked better) I am also having trouble finding a decent video driver for my ubuntu machine. Right now i'm at 640x480 as my only option and it is driving me crazy. The computer I am using has intel extreme graphics 6.14 from what I can tell, it's an older compaq(S4000NX). I desperatly need help. I really want to start using linux more then what I am using it for but right now I seem to be stuck with the preinstalled software. Thanks for any help anyone can offer me.

Dustin.

---

### Post by Xian on 2006-03-05
[QUOTE=dbrewer]I have been trying to search for help on exactly how to install new software on linux.[/quote]

Read the [Synaptic How-To](https://wiki.ubuntu.com/SynapticHowto) at the wiki for some answers.

[QUOTE=dbrewer]Right now i'm at 640x480 as my only option and it is driving me crazy. [/QUOTE]

Open a terminal (Alt + F2, then enter 'gnome-terminal') and issue the command below. It will walk you through the gfx setup and configuration. Be sure you have your monitor specs and other gfx info at hand. My guess would be that the install scripts didn't correctly detect your hardware and defaulted to the most base setting.

$ sudo dpkg-reconfigure xserver-xorg

---

### Post by joshuapurcell on 2006-03-05
The easiest way to install programs is to use Synaptic (System -> Administration -> Synaptic Package Manager). This shows you what is installed and what things you can install (depending on the repositories you have listed in your /etc/apt/sources.list file). Synaptic is just a graphical front end to the apt-get command, which can be run from a command line like this:```
sudo apt-get install firefox
```Firefox is used as an example, but whatever you want goes there. If you already have a .deb file, you can use the dpkg command like this:```
sudo dpkg -i nameOfPackage.deb
```This won't automatically take care of dependencies like Synaptic/apt-get would, but you may already have any dependencies taken care of (you'll get a message if you need other packages).

---

### Post by mh10190 on 2006-03-05
Ive always had problems installing software also
Synaptic is great
but there is some software that isnt there
like
i cant find the new firefox 1.5

but i downloaded the tar.bz2 (i think thats wat its called)
and i cant install it

my main question is

how to i install from the tar.bz2 file
and how do i remove previous versions of software

---

### Post by Bartender on 2006-03-05
dbrewer -
Did a quick Search using "640X480"...
Does this How-To help any?

[http://www.ubuntuforums.org/showthread.php?t=83973&highlight=640X480](http://www.ubuntuforums.org/showthread.php?t=83973&highlight=640X480)

Good luck

---

### Post by Xian on 2006-03-05
[QUOTE=joshuapurcell]This won't automatically take care of dependencies like Synaptic/apt-get would...[/QUOTE]

There's a sweet proggy in Dapper called gdebi that will help this situation.
Just FYI down the road....

---

### Post by tim15856 on 2006-03-05
[QUOTE=mh10190]Ive always had problems installing software also
Synaptic is great
but there is some software that isnt there
like
i cant find the new firefox 1.5

but i downloaded the tar.bz2 (i think thats wat its called)
and i cant install it

my main question is

how to i install from the tar.bz2 file
and how do i remove previous versions of software[/QUOTE]

Automatix will install Firefox 1.5. It's the easiest way to do it. It fixed a lot of problems I was having with various programs. [http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

"39*) Installs Firefox 1.5.0.1 and its plugins(themes and extensions are not retained, bookmarks need to be copied from backup folder)
40*) Installs Mozilla-Thunderbird 1.5 (US-only version) (no support for non-US-english language packs and enigmail)"

---

### Post by mh10190 on 2006-03-05
WOW
Automax is amazing
extremly helpful
Thanx

but im still wondering how to install from source tarball
it would be good to know for the future
thanx

for example 
i downlaoded flock
its a tar.gz file
how do i install it

---

### Post by aysiu on 2006-03-06
Read this:
[http://www.psychocats.net/linux/installingsoftware](http://www.psychocats.net/linux/installingsoftware)

---

