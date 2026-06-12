---
title: "Apt-get query"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-08-23
Hi all

This may seem like a strange question but there is logic behind it. Does the apt-get process use any other ports that port 80 (HTTP)?

Currently through my router I cannot access the repositories if I use a http address if i use the fto version of one of the repository addresses i can access it fine. I know this is not a fault with my ubuntu as this is only a problem when i am going through my router so i am wondering if i need to open some ports up.

I dont think i need to but i just want to check before i start checking out my router.

cheers
niteblind

---

### Post by N6546R on 2006-08-23
I just did an apt-get update and apt-get install while capturing packets with ethereal. Looks like apart from DNS queries for the archive hosts, it's all port 80 outbound when using http in sources.list.

Which repositories are you haveing trouble with?

Perry

---

### Post by niteblind on 2006-08-23
hi

cheers for that i am currently not at home so i cannot give you the exact addresses but from the default sources.list file it was all the security packages that failed on install and on a later apt-get install as well. It seems to connect and then simply gets no response.

As i said i KNOW  the fault lies in the router as if i connect directly to my cable modem i can access the exact same addreses without issue.  It is not an actual issue as i have a sources.list set up all with ftp addresses of the relevant servers and it works fine so it isnt like i cant update it is just annoying so i want to get to the bottom of it.

Cheers
niteblind

---

### Post by museum_geek on 2006-08-23
Hi,

I have a similar problem in that I cannot install any updates or packages.  Synaptic doesn't seem to connect.  apt-get has the same problem.  It seems to freeze when they try to connect to the [http://.](http://.)......  This is kinda weird, because I can browse the Internet using Firefox without any problems.

It has been very annoying because I installed Ubuntu two days ago and would like to install a lot of packages.  

Do you guys know how to fix this?  I tried running Gaim and that doesn't seem to connect either.  I've tried disabling IPv6 for all applications, but....no luck.

How do you access the ftp thingy?? I wanna try to install all the packages I need...e.g. gcc, latex, xmms and all other essential stuff. 

Thanks,

---

### Post by gils0040 on 2006-08-23
check your dns settings and make sure they are correct.

---

### Post by niteblind on 2006-08-23
it is unliklely to be DNS for two reasons;
1. The DNS resolutions are provided by the same server with and without the router.
2. The FTP addressing of the sources.list are the same it is only the protocol used that i have changed but thanks for the idea anyways.


museum_geek i will PM you when i get home with a sources list i am using.

nit eblind
niteblind

---

