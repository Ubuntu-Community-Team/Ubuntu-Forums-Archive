---
title: "Help installing FreeNX"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Thanh Nguyen on 2007-12-28
Hi all,

unbuntu has been great.  I will be donating some money soon.  But first I need to get somethings running on my old computer a 500mhz ppc ibook.

Installed 6.06 xubuntu fine.  Everything worked fine. Love it.

Now I want to install freenx on it.

follow instruction from community
[B]
installing the FreeNX server

gksudo gedit /etc/apt/sources.list

For Ubuntu 5.10 and 6.06, they are:

deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
deb-src [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx[/B]

update list

I have to compile my own since this is a ppc no package are  available
I have no idea how to build one!  

so i followed the instruction

to get the source code from the following repository and and compile my own.  I check the respository and the source file is there but somehow I was not able to pull the code from there.

I get the following error
**Failed to fetch [http://free.linux.hp.com/~brett/seveas/freenx/dists/dapper-seveas/Release](http://free.linux.hp.com/~brett/seveas/freenx/dists/dapper-seveas/Release)  Unable to find expected entry  freenx/binary-powerpc/Packages in Meta-index file (malformed Release file?)**

so i could not get the source to 
[B]sudo apt-get build-dep nx freenx
apt-get -b source nx freenx[/B]

I am an absolute newbie  thanks a million for all your help. :):KS:guitar::popcorn:

---

### Post by bodhi.zazen on 2007-12-28
I moved you post to a more visible location.

First, welcome to Ubuntu :)

Donations are always nice, but are not required.

> Just a comment about Linux being "free". Yes it is true, but are you willing to contribute to the cause?

By that I only mean to point out that many of the applications in the open source community are written and maintained by developers.

If you like this service consider donating 25-50 $ yearly to your favorite developer, application, ubuntu, whatever. This will keep the Linux community going and is certainly a  small investment in return for the service. Think of like contributing to NPR or PBS.

...The beer may be free, but you should tip the bartender 8)

Back to your original question, I can not help with freenx as I have had problems with it. There are a number of folks here, however, who use it and I hope they will help.

You could try an alternate such as SSH or an alternate VNC server / viewer :

[uwiki]VNC[/uwiki]

[uwiki]SSHHowto[/uwiki]

HTH :)

---

### Post by Thanh Nguyen on 2007-12-30
thanh you very much for you reply.

I will be trying  vnc then.

Hopefully it will be easier.

I will agree with you 100% about  tipping the bartender.

Installing is easy but configuring just tough!

Thanks a million.

:popcorn::(:):guitar::KS

---

