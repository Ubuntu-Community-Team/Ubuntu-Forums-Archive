---
title: "Is Ubuntu relocateable?"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by gobuntu on 2007-08-31
Dear friends,

I have Ubuntu 7 in my laptop and am preparing to install Ubuntu Server Edition on an older 386 desktop, want LAMP but with PostgreSQL. (It's downlloading right now).

I consider this sort of a preliminary/learn installation and I have these questions for which will appreciate help.

1. The installation I contemplate is LAMP with MySQL, as packaged. Do I just install PostgreSQL and leave MySQL as is?

2. I suppose Apache already will be set-up for PHP, but do I need to make Apache aware of PostgreSQL?

3. Do I need to make PHP aware of PostgreSQL? 

4. Also: Is Ubuntu Server Edition relocateable once installed and used to another PC? How about the regular Ubuntu (not server)? This has to do with improving hardware later on.

I don't suppose that installing PostgreSQL in the Ubuntu Server as planned takes care of these things, however, please correct or confirm, or advise, if you please would, on what I may be missing.

In case there's a way to setup a server with PostgreSQL (rather than MySQL) that takes minutes and not hours or days, as explained for LAMP, please advise too. I don't mind, though, if MySQL is also installed, though.

The plan is to learn PostgreSQL in Linux with the server having those installations together, and then be able to access them from a second not-server pc, Linux or Windows web-browsers.

First, though, I just would like to install the Server, and it will be on a clean disk, with no critical data, all of this just for self-learning. 

Thank you!

---

### Post by C.S.Cameron on 2007-09-01
Not totally sure of the question, but I use Ubuntu installed on a USB flash drive and it boots on different computers.

---

### Post by wirelessmonkey on 2007-09-01
1) Sure, just make sure to set up your PostgreSQL administration, i.e. root pass
2)Does Apache need to be aware of either, really? Isn't it the next layer of application that interacts w/ any database?
3)Yes, depending on how php was compiled, but if you use the repositories, this is generally taken care of automatically, else you'll have to recompile PHP with the correct options.
4)It depends on how big a change takes place.  If there is any major architecture change (processor, motherboard, others?) then the easy route would be to backup your important files/configurations and reinstall.  This may not be strictly necessary though.

I run PostgreSQL and MySQL, and haven't really had any issues.

---

### Post by gobuntu on 2007-09-01
> **wirelessmonkey said:**
> 1) Sure, just make sure to set up your PostgreSQL administration, i.e. root pass
2)Does Apache need to be aware of either, really? Isn't it the next layer of application that interacts w/ any database?
3)Yes, depending on how php was compiled, but if you use the repositories, this is generally taken care of automatically, else you'll have to recompile PHP with the correct options.
4)It depends on how big a change takes place.  If there is any major architecture change (processor, motherboard, others?) then the easy route would be to backup your important files/configurations and reinstall.  This may not be strictly necessary though.

I run PostgreSQL and MySQL, and haven't really had any issues.

Dear wirelessmonkey,

Thanks for the help.

1. I noticed on my Windows XP that MySQL and PosgreSQL are processes running. I don't know much on what this means, but in Linux it will probably be the same? Now, if I don't need MySQL for a time, does a process running use-up memory in Linux? Does it pose any security liability, specially in a server, to have processes running that are not really needed?

2. Good explanation. Thanks. I do gather this would be what's called 3-tier aproach? Now, what's got me a little confused is the use of the word 'server' for all these things: Apache Server, PostgreSQL server, and then Ubuntu-Server. I am about to install Ubuntu-Server Edition, which I am not quite clear on what it does without Apache-Server, and without say PosgreSQL-server. And then I read about TomCat-Server, and the word 'server' is all over. Can someone briefly state what the Ubuntu-Server without any extras installed basically does? Is it much like the Server in old local-area networks, prior to the web? Now, in an Ubuntu non-server machine, I can still run the Apache-Server, and the PosggreSQL-server, even if that machine is NOT a server? 

4. On relocatable, I realize that there are limits, but I suppose and am interested in confirmation that if I make an image of the server's hard disk, I could clone that image into an identical, or similar clean hard disk with equal or more storage space. I mean I will start with a rather small hard-disk at hand, and depending on how things go, I hpope I can clone it into a larger disk.

As far as relocation via USB stick, or a live-CD, no, that's not what I mean. I also realize that an installation is hardware-dependant. However, on Windows-Xp, the installation reads something like a 'serial number' (or whatever) from a machine, so that one can not dup Windows from one machine into several identical ones. I haven't tried it, but that's what I've heard. So, I hope Linux is not as such.

Thanks fellows for your understanding, specially as it relates my being obsolete from using older systems, sometimes old-knowldege gets in the way.:mad:

---

### Post by wirelessmonkey on 2007-09-01
1) Yes, they do run as processes.  But... if MySQL isn't doing anything, the memory footprint will be negligible. That being said, if you're not using MySQL for anything, it would be best to turn it off.
2) Yeah, the terminology isn't truly clear. Each use of 'server' is contextual.  You have a physical Server, a device connected to a network that "servers" information to outside users.  You have MySQL, PostgreSQL, and Apache "servers" which run on the physical 'server', which are applications that provide the data requested from the physical server.  The major difference between Ubuntu-Server and Ubuntu-Desktop is the lack of a graphical user interface like GNOME or KDE, with a few  (if I recall correctly) security optimizations for the server.

4) You can absolutely image your hard drives, and expect that they will be portable to another hard drive of the same or greater size.  I recommend partimage!  There are many other imaging solutions, and backup solutions if you prefer.

---

### Post by Skrynesaver on 2007-09-01
> **gobuntu said:**
> Dear wirelessmonkey,

Thanks for the help.

1. I noticed on my Windows XP that MySQL and PosgreSQL are processes running. I don't know much on what this means, but in Linux it will probably be the same? Now, if I don't need MySQL for a time, does a process running use-up memory in Linux? Does it pose any security liability, specially in a server, to have processes running that are not really needed?

If a computer is exposed to the internet you shouldn't have any unnecessary  process running particularily one which listens to the network for commands.  So either uninstall MySQL or remove it from your  runlevel.  This can be done by removing the symlink S??mysqld in /etc/rc3.d/ or whichever is your default runlevel.
> 
2. Good explanation. Thanks. I do gather this would be what's called 3-tier aproach? Now, what's got me a little confused is the use of the word 'server' for all these things: Apache Server, PostgreSQL server, and then Ubuntu-Server. I am about to install Ubuntu-Server Edition, which I am not quite clear on what it does without Apache-Server, and without say PosgreSQL-server. And then I read about TomCat-Server, and the word 'server' is all over. Can someone briefly state what the Ubuntu-Server without any extras installed basically does? Is it much like the Server in old local-area networks, prior to the web? Now, in an Ubuntu non-server machine, I can still run the Apache-Server, and the PosggreSQL-server, even if that machine is NOT a server? 

A computer which is a server is one which is used for that purpose,.

An operating system which is a server is similarly defined by use, but generally is one with all the userland tools removed and optimised for a specific role.

An application which is a server is one which listens on a port for requests directed to it from the network and responds to those requests in dome way.

Hope that's as clear to read as it is in my head ;)
> 
4. On relocatable, I realize that there are limits, but I suppose and am interested in confirmation that if I make an image of the server's hard disk, I could clone that image into an identical, or similar clean hard disk with equal or more storage space. I mean I will start with a rather small hard-disk at hand, and depending on how things go, I hpope I can clone it into a larger disk.

As a general rule servers are partitioned so that the data portion that is served is kept on a separate partition which is backed up regularly and can be dd'd on to another machine with a similar setup.  This is what I would advise in this situation, as it gives you a quick route to recovery in the event of disaster.

---

### Post by gobuntu on 2007-09-01
> **wirelessmonkey said:**
> 1) Yes, they do run as processes.  But... if MySQL isn't doing anything, the memory footprint will be negligible. That being said, if you're not using MySQL for anything, it would be best to turn it off.
2) Yeah, the terminology isn't truly clear. Each use of 'server' is contextual.  You have a physical Server, a device connected to a network that "servers" information to outside users.  You have MySQL, PostgreSQL, and Apache "servers" which run on the physical 'server', which are applications that provide the data requested from the physical server.  The major difference between Ubuntu-Server and Ubuntu-Desktop is the lack of a graphical user interface like GNOME or KDE, with a few  (if I recall correctly) security optimizations for the server.

4) You can absolutely image your hard drives, and expect that they will be portable to another hard drive of the same or greater size.  I recommend partimage!  There are many other imaging solutions, and backup solutions if you prefer.

Thanks WM for your reply.

1. Am happy it's like you say. No real load, if I want to leave it as is. I don't mind learning MySQL but so far PostgreSQL will be first try.

2. Good explanation checks with what I was falling into. So there's no special Linux-Server operating system. Linux is only one, and it's multi-user, multi-tasking, and networkable since the beginning, unlike old DOS which was single-user and we had to use Novel, or networking software from others. I like your term 'physical server' which is my understanding of  'server';  in Linux it's a machine dedicated to centralised data management and sharing, still running Linux, and maybe different versions and distros of Linux can be running in different machines, and even a Windows machine can be connected to that physical Linux server.  Then Apache-'server', and PG-'server', and TomCat-'server' and the likes  boil dow to applications. My head is un-blocking.:)

4. I am happy to hear you confirm that  a hard-disk Linux installation can be relocated via imaging. I have done this in Windows with a software called True-Image but it still can not image the hard disk in which Windows is running. We have to remove the disk and iamge it in another Windows computer. I believe that that software can image a disk that has Linux and Windows, and maybe it can image a pure-linux disk if I remove it and USB-it to a Windows pc. But I am happy that Linux has this type of softwares too, and maybe even better. But, as is obvious, I am not there yet.

I think I'm ready to go for a Linux machine set up as physical server,  and meet the Devil in the details.

Bowing  in appreciation.

---

### Post by gobuntu on 2007-09-01
> **Skrynesaver said:**
> If a computer is exposed to the internet you shouldn't have any unnecessary  process running particularily one which listens to the network for commands.  So either uninstall MySQL or remove it from your  runlevel.  This can be done by removing the symlink S??mysqld in /etc/rc3.d/ or whichever is your default runlevel.

A computer which is a server is one which is used for that purpose,.

An operating system which is a server is similarly defined by use, but generally is one with all the userland tools removed and optimised for a specific role.

An application which is a server is one which listens on a port for requests directed to it from the network and responds to those requests in dome way.

Hope that's as clear to read as it is in my head ;)

As a general rule servers are partitioned so that the data portion that is served is kept on a separate partition which is backed up regularly and can be dd'd on to another machine with a similar setup.  This is what I would advise in this situation, as it gives you a quick route to recovery in the event of disaster.

Thank you, Skrynesave!

I am better off on the meaning of 'server' now after all this help, I believe.

Also, I understand what you mean by data being separate, and backed up as often as possible. I am used to having it on separete subdirectories, but now realize that it being in a different partition is better, since it amounts to it being on a separate disk, almost. Yes, that's a very valuable tip.

Also, what you say about unnecessary processes that are available for input and control should best not be allowed for security reasons makes good sense. (We have quite a bit of that in Windows default installations, and 3d-party softwares,  with the added disadvantage that it is difficult to know what they are doing or why they're there,  and can and have lead to problems for end-users).

One great thing about Linux is that it's open and well documented. Vast, though.

It's great meet you all in this community!

---

