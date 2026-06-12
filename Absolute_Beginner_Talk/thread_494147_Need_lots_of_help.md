---
title: "Need lots of help"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Adam_V on 2007-07-06
First off I'm runing Ubuntu 5.10, yes I know this is really old but I screwed up my hd and was forced to install this. I like it so far and I want to install the latest version but am having severe problems. I have the iso but it's been compressed in a .rar format and I tried using wine to use winrar and some other programs but wine either doesn't load or has serious bugs. I have no idea how to install stuff besides using sudo apt-get install 'x' and synaptic doesn't show anything that I can download that can uncompress .rars. I downloaded the linux version of winrar but I have no idea how to install that (went to a bunch of sites and [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) was the only decent one and it didn't give instructions). My internet is slow so downloading a unrar'd iso would take days which I would prefer didn't happen. I found another .iso of kubuntu on a random cd (burnt the iso, not the contents :() so I tried reburning it using cdrecord which doesn't work and says that it doesn't run on versions of linux newer then 2.5 and I have 'Linux-2.6.12-9-386'. I did manage to use nautilus to burn a cd but the cd isn't bootable. I used wine to run poweriso and magiciso but neither work properly. So to anyone who doesn't want to read the above paragraph:

I am runing Ubuntu 5.1
I need to uncompress a .rar file which containts a .iso
I need to burn that .iso to a cd-rw and boot from it
I have no idea to do so :p

Help :p

---

### Post by Krosis on 2007-07-06
> **Adam_V said:**
> First off I'm runing Ubuntu 5.10, yes I know this is really old but I screwed up my hd and was forced to install this. I like it so far and I want to install the latest version but am having severe problems. I have the iso but it's been compressed in a .rar format and I tried using wine to use winrar and some other programs but wine either doesn't load or has serious bugs. I have no idea how to install stuff besides using sudo apt-get install 'x' and synaptic doesn't show anything that I can download that can uncompress .rars. I downloaded the linux version of winrar but I have no idea how to install that (went to a bunch of sites and [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) was the only decent one and it didn't give instructions). My internet is slow so downloading a unrar'd iso would take days which I would prefer didn't happen. I found another .iso of kubuntu on a random cd (burnt the iso, not the contents :() so I tried reburning it using cdrecord which doesn't work and says that it doesn't run on versions of linux newer then 2.5 and I have 'Linux-2.6.12-9-386'. I did manage to use nautilus to burn a cd but the cd isn't bootable. I used wine to run poweriso and magiciso but neither work properly. So to anyone who doesn't want to read the above paragraph:

I am runing Ubuntu 5.1
I need to uncompress a .rar file which containts a .iso
I need to burn that .iso to a cd-rw and boot from it
I have no idea to do so :p

Help :p

Applications > Add/Remove (hopefully that was in 5.1) and download these.

7zip to uncompress your .rar
k3b to burn your iso to a cd
Restart your computer.

---

### Post by Adam_V on 2007-07-06
> Application 'k3b' not available

The application can not be found in your archive. This usually means that it is not available for your hardware plattform

7zip isn't listed

---

### Post by Krosis on 2007-07-06
> **Adam_V said:**
> 7zip isn't listed

Is anything listed when you search for RAR?  I see: RAR, Archive Manager, Ark, KAcrhiver, and 7zip.

Are any of those listed?

---

### Post by annda on 2007-07-06
it looks like unrar is in breezy's repositories:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unrar&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unrar&searchon=names&subword=1&version=breezy&release=all)

after you install that, file roller should nicely handle rar files.

actually, k3b should be available too:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=k3b&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=k3b&searchon=names&subword=1&version=breezy&release=all)

have you tried synaptic or plain old terminal?

```
sudo apt-get update
sudo apt-get install unrar k3b
```

---

### Post by Adam_V on 2007-07-06
I used both the terminal and synaptic.

> Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

> adam@ubuntu:~$ sudo apt-get install k3b
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package k3b


---

### Post by annda on 2007-07-06
do you have all the repositories enabled?

if you have the right version of libc, you can download the .deb from here:
[http://packages.ubuntu.com/breezy/utils/unrar-free](http://packages.ubuntu.com/breezy/utils/unrar-free)

and install via mouse-click.

---

### Post by Adam_V on 2007-07-06
Only one I have enabled is breezy badger. How do I get more?

---

### Post by forrestcupp on 2007-07-06
To enable repositories type:
```
gksudo gedit /etc/apt/sources.list
```
and uncomment all of the repository lines.  You uncomment a line by deleting the # at the beginning of that line.  The repository lines are the ones that start with deb.

When you're done, save it, and update apt
```
sudo apt-get update
```
then see if unrar is available after doing all of this.

---

### Post by Adam_V on 2007-07-06
The list is blank. Where can I go to figure out what to put in it?

I went to the site Annda linked to and installed unrar. 

> adam@ubuntu:~$ unrar-free --extract /home/adam/Desktop/Ubuntu.rar

unrar 0.0.1           Copyright (c) 2004 Ben Asselstine


Extracting from /home/adam/Desktop/Ubuntu.rar

All Ok


Nothing happened. And it said 'all ok' instantly so I don't think it extracted? Can someone give me an example?

Also I went to

[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fk%2Fk3b%2Fk3b_0.12.2-0ubuntu2_i386.deb&md5sum=86a0f247165b954234bc5d32335c5c86&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fk%2Fk3b%2Fk3b_0.12.2-0ubuntu2_i386.deb&md5sum=86a0f247165b954234bc5d32335c5c86&arch=i386&type=main)

But none of the mirrors work for me

And I tried installing the AMD version of unrar but it said to get in Intel one but I have an amd processor?

---

