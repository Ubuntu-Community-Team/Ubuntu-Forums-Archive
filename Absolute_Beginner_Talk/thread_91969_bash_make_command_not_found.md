---
title: "bash: make: command not found"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by swisscheez on 2005-11-18
I've looked all over for what probably is a very easy thing to solve... but, I've become exhausted with the search and am now seeking help.

I'm sure this is very simple but how does one install "make"?

---

### Post by Kvark on 2005-11-18
```
sudo apt-get install build-essential
```

---

### Post by Trunk_z on 2005-11-18
I think if you just want the "make" command you can use:

sudo apt-get install make

Open the Terminal program and type the above in. sudo (I *think*) means that it enables the super-user or root for the command you type afterwards (in this case, 'apt-get'). So it will ask you for your root password, after that checks out it should download and install the specified program. (I think, I'm kinda new)

---

### Post by Kvark on 2005-11-18
Trunk_z yes you can install just make but he will probably need the other things that are "build essential" too. And yes sudo gives root access for the command that follows it but it wants the user's password and not root's password.

---

### Post by Trunk_z on 2005-11-18
Oh right, cool. Thanks for clearing those few things up O:)

---

### Post by swisscheez on 2005-11-18
That did it.  Thank you both.

---

### Post by Trunk_z on 2005-11-18
No problem

---

### Post by juanqui on 2005-11-22
I just installed kubuntu as well. For my internet connection to work I need to install a wireless network card, using ndiswrapper.

to install ndiswrapper I have to make use of the 'make' utility
Apparently 'make' has to be installed separately, for wich I need an internet connection...:confused: 

Is there a way to download the 'make' utility in windows, put it in a shared partition and install it in kubuntu?

---

### Post by Kvark on 2005-11-22
I think build-essential including make is included on the (K)Ubuntu CD. Put in the CD, make sure you have a line in /etc/apt/sources.list that says something similar to the one below and try to install it.
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```

---

### Post by juanqui on 2005-11-22
So I insert the CD_ROM, and then type

sudo apt-get install build-essential

or do I need to specify

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

first in /etc/apt/sources.list

---

### Post by narcolept on 2005-11-22
You would insert the cdrom, 

```
sudo vi /etc/apt/sources.list
```

and add deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted or the appropriate line for your cd.  Chances are it's still in there as the first line and commented out with a #.

```
sudo apt-get update
```

and then

```
sudo apt-get install build-essential
```

---

### Post by juanqui on 2005-11-27
Thanks! I managed to install build-essential. Now when I try the next step I get:

```
can't find kernel sources in /lib/modules/2.6.12.9.386/build
give the path to kernel sources with KSRC=<path> argument to make
```

This means I have to install the kernel source seperatly? I haven't got a clue how to do this to be honest. Since I haven't got the internet connection working yet I can't look for help easily and need to pray It works every time. Could someone please help me on this as well?

---

### Post by ssam on 2005-11-27
have a look at
[http://www.ubuntuforums.org/showthread.php?t=45579](http://www.ubuntuforums.org/showthread.php?t=45579)

there are lots of answer to common questions on the forums if you have a good look.

---

### Post by juanqui on 2005-11-27
I have a FAT32 partition to communicate with WINDOWS so getting the package is not the problem. What I'm not sure of is if I need the source or just have to edit some config file. How do I find out what kernelsource I need - provided this is what I have to install. Or can't you install a kernelsource - for I don't want it to be compiled (do I). In short I am an absolute nitwit (still).

I had a look on some of the similar questions but the answers are either to complicated or the problem is a config thing

---

