---
title: "Any distro like Ubuntu but with dev stuff?"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by outofsync on 2006-03-24
Hi,

I see another user in a similar situation has posted a related question today. Here goes mine:


My question (short format): Do you know of any Linux distribution as easy to install/configure/use as Ubuntu, but with an installation CD that includes all the packages needed for compiling X11/Xt/OpenGL apps?


My question (again, but in long format, explained):

I installed Ubuntu, and, first of all, my sincere congratulations to the Ubuntu team because installation is really straightforward, and everything works.

However, I need to compile software, and my Linux box isn't connected to internet, nor will be in the future.

I installed the "build-essential" stuff. However, that's not enough for compiling X11 applications. All the X11 dev stuff isn't included in the CD. Some must-have packages like bison and flex aren't there either.

I know about the Ubuntu archive website, but dependencies are a nightmare... you begin to follow links, and more links, and then some more, and the tree never seems to end.

Is there any Ubuntu site with CD images that have the stuff not included in the installation CD, so that I don't need to worry about dependencies?

Otherwise, I guess my only option will be to look for another distribution... suggestions welcome.

---

### Post by aragorn2909 on 2006-03-24
[QUOTE=outofsync]
My question (short format): Do you know of any Linux distribution as easy to install/configure/use as Ubuntu, but with an installation CD that includes all the packages needed for compiling X11/Xt/OpenGL apps?
[/QUOTE]
I do believe that a full install of Slackware includes everything you need for this sort of thing.  That being said, however, Slackware *is* a little different to install and configure, but it is not nearly as difficult as some would make it out to be.

A

---

### Post by akiro.yamamoto on 2006-03-24
I think SUSE comes with the dev packages and it's relatively easy to configure and maintain.

---

### Post by aragorn2909 on 2006-03-24
[QUOTE=akiro.yamamoto]I think SUSE comes with the dev packages and it's relatively easy to configure and maintain.[/QUOTE]
OpenSuse install = 4-5 disks
Slackware install = 2 disks

I do like Suse (alot) though, and am running it on my main box at the moment.

---

### Post by akiro.yamamoto on 2006-03-24
Hah I'm tri-booting SUSE 10 ,OSX x86 and Ubuntu 5.10 ;)
But Slackware is still one of my favs.... ;)

---

### Post by dcraven on 2006-03-24
The brand new Fedora Core 5 (with new GNOME and all the good stuff we love) has a full install package of multiple disks too... Like 5 or something mental if memory serves correct. I'd hope that the dev packages are included on that. This might be the current closest thing to Ubuntu in terms of similar current packages. It is an RPM based distro (like Redhat) instead of a DEB based distro (like Debian) if that matters at all.

~djc

---

### Post by stuporglue on 2006-03-24
You might be able to download the Debian Cds and use them on your Ubuntu. You can download the entire Debian repository on CD. It's about 7 disks of binaries, and maybe another 7 of source.

---

### Post by aragorn2909 on 2006-03-24
[QUOTE=stuporglue]You might be able to download the Debian Cds and use them on your Ubuntu. You can download the entire Debian repository on CD. It's about 7 disks of binaries, and maybe another 7 of source.[/QUOTE]

14 disks, for someone with no internet connection?  Yikes!

---

### Post by Brunellus on 2006-03-24
[QUOTE=outofsync]Hi,

I see another user in a similar situation has posted a related question today. Here goes mine:


My question (short format): Do you know of any Linux distribution as easy to install/configure/use as Ubuntu, but with an installation CD that includes all the packages needed for compiling X11/Xt/OpenGL apps?


My question (again, but in long format, explained):

I installed Ubuntu, and, first of all, my sincere congratulations to the Ubuntu team because installation is really straightforward, and everything works.

However, I need to compile software, and my Linux box isn't connected to internet, nor will be in the future.

I installed the "build-essential" stuff. However, that's not enough for compiling X11 applications. All the X11 dev stuff isn't included in the CD. Some must-have packages like bison and flex aren't there either.

I know about the Ubuntu archive website, but dependencies are a nightmare... you begin to follow links, and more links, and then some more, and the tree never seems to end.

Is there any Ubuntu site with CD images that have the stuff not included in the installation CD, so that I don't need to worry about dependencies?

Otherwise, I guess my only option will be to look for another distribution... suggestions welcome.[/QUOTE]
is the host that you intend to use for development connected to the internet?

if so, why not just use apt?

---

### Post by SSTwinrova on 2006-03-24
[QUOTE=Brunellus]is the host that you intend to use for development connected to the internet?

if so, why not just use apt?[/QUOTE]

"and my Linux box isn't connected to internet, nor will be in the future."

---

### Post by outofsync on 2006-03-24
[QUOTE=aragorn2909]14 disks, for someone with no internet connection?  Yikes![/QUOTE]
I have a good internet connection, but not on the machine used for development. 

I used slackware many years ago. And RedHat 7. However, none of these distributions worked "out of the box" (at least some years ago, they required manual work because some drivers didn't work, or some hardware wasn't detected, or something didn't work as expected, etc...)

I'm greatly impressed by Ubuntu because everything worked without any need of spending additional time in manual adjustments.

The lossless repartitioning tool is also great. Included in the installation CD, and worked as expected.

I just want this ease, but with downloadable CD (or DVD) images of all the stuff needed for compiling the usual open source applications.

---

### Post by stuporglue on 2006-03-24
[QUOTE=outofsync]I have a good internet connection, but not on the machine used for development. 

I'm greatly impressed by Ubuntu because everything worked without any need of spending additional time in manual adjustments.

I just want this ease, but with downloadable CD (or DVD) images of all the stuff needed for compiling the usual open source applications.[/QUOTE]

I assumed you had a connection of some sort since you were shopping for a distro, or something. 

Ubuntu is based on Debian. Compatilibity with the current Debian repos is not guaranteed, but is usually funtional from what I hear. I think you should be able to ...

1) Download the CDs and add them to your Ubuntu synaptic
2) Disable the online repositories for your Ubuntu synaptic
3) Add and remove whatever packages were available on the Debian CDs through synaptic

If you like Ubuntu and need everything to be available offline, that's what I'd recomend. You can probably find out which packages are on which Cds and not download them all, just the ones you want.

---

### Post by YuHoo on 2006-03-24
I'm not 100% sure about this but I've been told that the two best distros for developing are slackware and vector Linux. If you have $5 you can always buy the cds online.

---

