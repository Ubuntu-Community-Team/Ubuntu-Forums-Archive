---
title: "Desktop on Server without Internet"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by guido68 on 2007-03-30
Simple.... or so I thought. Have installed LAMP install of Server 6.10
Now I want to add ubuntu-desktop to it.
My PC is not connected to the internet and for some reason the sources.list file is empty.
I have also downloaded the desktop iso.

So how to I go about installing the desktop onto the server edition!???

There are a couple of things I have found inc. apt-get and from the docs on the server cd which say to run:
$ sudo tasksel install ubuntu-standard
$ sudo tasksel install ubuntu-desktop

but this presumes that these sources are available. Is it possible to use the desktop iso as source??? as [http://.](http://.).. blah sources I cannot access.

Thanks for any help to a ubuntu noob!!!

---

### Post by tonym on 2007-03-30
Use

apt-cdrom add

to tell apt-get about your CD.  This should add to /etc/apt/sources.list.  Then do

apt-get install ubuntu-desktop

However,  not sure if the desktop CD will work for this.  You may need to download the "alternate" CD.

Regards

Tony

---

### Post by guido68 on 2007-03-30
Thx.... have found a DVD Iso whcih appears to have all the packages on it... so if I use apt to add this as source depot, then hopefully will find it all.

Just have to download the 3.5G iso now and see if it works.

the iso I am going to get is here:
[http://cdimage.ubuntu.com/releases/edgy/release/](http://cdimage.ubuntu.com/releases/edgy/release/)

I guess this has all desktop and server componenents on it :confused:

---

### Post by az on 2007-03-30
> **guido68 said:**
> 
My PC is not connected to the internet and for some reason the sources.list file is empty.
I have also downloaded the desktop iso.


The desktop iso is an operating system on a disk.  It is not a repository from which you can install packages.  The alternate cd is a repository of packages along with an installer.

> **guido68 said:**
> 
So how to I go about installing the desktop onto the server edition!???



Download the alternate cd and do as stated in the previous post.

As well, you probably would need to install the desktop kernel, since some home-computer hardware does nto work with the server kernel:

sudo apt-get install linux-generic

---

### Post by guido68 on 2007-03-30
Thanks... its going on a Dell PE600SC... which is lowest of the low server.. want to use it at home as general purpose web server, media server, blog hosting all around play box! Used UNIX proper (Solaris/HPUX) but quite a while ago and also played a bit with RedHat so hopefully wont take me too long to getg back up to speed!

---

