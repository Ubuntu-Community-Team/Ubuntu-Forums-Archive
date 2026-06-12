---
title: "Can someone explain a few things about packages please?"
date: 2005-08-24
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2005-08-24
Hi,
I'm and impressed with Ubuntu. (love it).

Anyway, everything I have installed so far has been through commands found in ubuntuguide.org.

Wanting to know what other programs are available I looked into Synaptic Package Manager.

There I noticed that for different sections there are 2-3 different options. For example: there is Development, Development (restricted), and Development (universe).

Can someone explain to me what the differense is? Which ones do we install? Do we just look at a package name and run the "sudo apt-get install" command?

What if we just download a package off the net. What extention does it have to be? not .rpm right? And how do we install it then? Aren't there dependencies? Noticed that with the apt-get install dependencies are taken care off... am I right?

So everything that's in the universe available to ubuntu users is listed under this package manager?

---

### Post by vruum on 2005-08-24
Hi.
I don't know all of it, but here goes, the difference between Development and Development-universe, the universe is a community maintained repository, it's not activated by default so you may remember doing it, following the ubuntuguide, 
([http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)) that it's community maintained means that it's not officially supported. It provides packages that are not in the official repositories for various reasons, even package maintainers don't have unlimited time, also there may be some licensing issues that prohibits official distribution. 
Apt-get install, i think, goes through your /etc/apt/sources.lst, and if it finds two or more instances of the same package name (different versions), asks you to choose which version you want to install. 
If you download a package of the net, it should have a .deb extension, (as in DEBian, the linux-distribution that ubuntu is based on. some programs have ubuntu specific .deb packages) install deb packages with this command.
sudo dpkg -i <package-name.deb>
it wont install dependencies, but it will tell you what you're missing, if any. installed *.debs will show in synaptic
It's also possible to install from source-code (typically .tar.bz2 og *.tar.gz packages) 
But, generally speaking, the bestest and safest way to install anything is from apt-get/synaptic, so to begin with you should probably stick with that.

---

### Post by Lord Illidan on 2005-08-24
[QUOTE=ROUBOS]Hi,
I'm and impressed with Ubuntu. (love it).

Anyway, everything I have installed so far has been through commands found in ubuntuguide.org.

Wanting to know what other programs are available I looked into Synaptic Package Manager.

There I noticed that for different sections there are 2-3 different options. For example: there is Development, Development (restricted), and Development (universe).

Can someone explain to me what the differense is? Which ones do we install? Do we just look at a package name and run the "sudo apt-get install" command?

What if we just download a package off the net. What extention does it have to be? not .rpm right? And how do we install it then? Aren't there dependencies? Noticed that with the apt-get install dependencies are taken care off... am I right?

So everything that's in the universe available to ubuntu users is listed under this package manager?[/QUOTE]

It is possible to download and install rpms, because Ubuntu has a program called alien which can convert rpms to .deb files. However, you should find almost every program you will ever need in synaptic.

---

### Post by Kvark on 2005-08-24
[QUOTE=ROUBOS]Do we just look at a package name and run the "sudo apt-get install" command?[/QUOTE]
When you already have synaptic open it's probably faster to mark the package for installation there by clicking on the checkbox next to the program and then click apply.

---

### Post by Chapita on 2005-09-22
[QUOTE=Lord Illidan]It is possible to download and install rpms, because Ubuntu has a program called alien which can convert rpms to .deb files. However, you should find almost every program you will ever need in synaptic.[/QUOTE]

I can't find alien, where is?

Anyway, I'm trying to install Real Player, from synaptic, but in the install process ask me the path where Real was downloaded or a .rpm file. 
I'm lost...

Thanks! ](*,)

---

### Post by traderjb on 2005-09-22
I'm in the same boat, synaptic has version 8.  I downloaded the RealPlayer 10 from Real.com, but for somereason the .bin file isn't working.

---

### Post by earobinson on 2005-09-22
alian is a terminal command type "man alian" for more info

---

