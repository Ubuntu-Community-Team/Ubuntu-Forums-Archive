---
title: "Going for BSD. What do I need to know?"
date: 2007-02-16
forum: BSD
---

### Post by brucevangeorge on 2007-02-16
I would like to try out FreeBSD. I hear its a speed demon compared to Linux.

What is it like?

Can I install some GUI for it? One made for the BSD kernel?

Also, can I select the file system it uses. I like fast performing file systems because my machine isn't the best money can buy so I want to get the most out of it. I used JFS in Ubuntu... does FreeBSD have something like this?

Also, how is wireless support for it? I have a dLink card that uses the Atheros chipset. Any Atheros drivers native to FreeBSD?

Also, what native software os available for it? Things like banshee, amark, rhythmbox... etc.

-Bruce

---

### Post by manmower on 2007-02-16
It uses the X server just like Linux so you can install Gnome or KDE... or another WM/DE.

I believe it defaults to UFS, don't know what other systems it supports, but I'd expect it to be quite a bit.

Atheros is available, last time I used it it used madwifi.

A lot of software is available, both as binaries or to compile for yourself. Also, Linux binaries are compatible with BSD.

---

### Post by brucevangeorge on 2007-02-16
> **manmower said:**
> It uses the X server just like Linux so you can install Gnome or KDE... or another WM/DE.

I believe it defaults to UFS, don't know what other systems it supports, but I'd expect it to be quite a bit.

Atheros is available, last time I used it it used madwifi.

A lot of software is available, both as binaries or to compile for yourself. Also, Linux binaries are compatible with BSD.

I also hear that linux needs to be emulated. Emulation = bottleneck from my experience.

Any native software that is actually good?

---

### Post by runningwithscissors on 2007-02-16
> **brucevangeorge said:**
> I would like to try out FreeBSD. I hear its a speed demon compared to Linux.
It is not significantly any "faster". There is no reason for it to be.

> **brucevangeorge said:**
> What is it like?
Quite nice. Feels very simple, clean, well-laid out, and has lots of very good documentation.

> **brucevangeorge said:**
> Can I install some GUI for it? One made for the BSD kernel?
KDE, GNOME, Xfce, *box, you know, the usual suspects. They all run natively.

> **brucevangeorge said:**
> Also, can I select the file system it uses. I like fast performing file systems because my machine isn't the best money can buy so I want to get the most out of it. I used JFS in Ubuntu... does FreeBSD have something like this?
It has support for reading and writing to some other filesystems. But only UFS2 installations are supported, I think. And it is a decent filesystem. No reason to not use it.

> **brucevangeorge said:**
> Also, how is wireless support for it? I have a dLink card that uses the Atheros chipset. Any Atheros drivers native to FreeBSD?
That can get hairy. Yes, Atheros drivers are availble. I don't use wireless, but I've heard that they can be a bit hit and miss.

> **brucevangeorge said:**
> Also, what native software os available for it? Things like banshee, amark, rhythmbox... etc
Almost all of those. Some apps may require a Linux compatibility layer, however. And there isn't any noticeable slowdown when using the compatibility layer.

---

### Post by handy on 2007-02-17
I found [***_PC-BSD_***]("http://www.pcbsd.org/") is really easy to install & setup. (Unless you have an ASUS A7N266-VM which has known issues.)

No hardware problems except for my original old M$ intellimouse explorer, which was erratic (as it is in Edgy too)?! My Logitech one works like a charm? Internet worked immediately  (unlike my regular Ubuntu experience) the whole thing was quicker & easier than my previous Ubuntu installs.

nVidia make native BSD drivers, later version than those for Linux! Flash-7 is also available for BSD.

The BSD's are not good for gamers who need Wine, Crossover or Cedega, YET.  The reason for this is that the Wine developers develop for Linux.  Linux native games run with no noticeable speed penalty. There is a limited selection of Native BSD games at this stage.

So, my Guild Wars gaming currently happens on my 2nd Edgy machine.* **[Edit:]** Fiesty herd 5 now* :-D

I have found that adding & setting up additional drives/partitions is still more difficult  than under Linux = there is no  utility with a GUI like Gparted & the like. But I managed to do it after a little research.

Also, along the same lines, if you want to make a /home,  /var or /usr ***partition*** you will need to use the command line tools for the job.  

The [***_PC-BSD_***]("http://www.pcbsd.org/") OS is clean & tidy with great documentation, it installs the KDE desktop environment, & is optimised to use same.

[***_PC-BSD_***]("http://www.pcbsd.org/") uses a unique (among the BSD's) install method, where installation files called [***_.pbi_***]("http://www.pbidir.com/") 's are chosen from a web site, downloaded & then double clicked on to run an installation file, requiring usually 2 more clicks & the installation is over.  [***_PBI_***]("http://www.pbidir.com/")'s usually install quite quickly, & have the benefit of bringing their dependencies with them.  This uses slightly more disk space for the added reliability & ease of installation.

For those that don't like the PBI method, [***_the FreeBSD ports_***]("http://www.freebsd.org/ports/linux.html") which include many thousands of softwares is also available, as well as being able to compile & make from source. **[Edit:]** *Linux software runs & as fast as on a native Linux box too!*

The [***_PC-BSD forum_***]("http://forums.pcbsd.org/index.php") is friendly & tiny, by comparison with the huge Ubuntu one.

[***_PC-BSD_***]("http://www.pcbsd.org/")'s aim is to be as easy as possible for the user to do what ever...  It is still young, but certainly good enough already to be my main OS.

---

### Post by x1a4 on 2007-02-27
Best way to experience and evaluate FreeBSD is to use it.  Get the FreeBSD Live CD called [FreeSBIE](http://www.freesbie.org/).

---

### Post by ihavenoname on 2007-03-13
Hey, I too am once again interested in this. Can you choose to install from binaries on freebsd or are you forced to build the first time? How long does it take?

---

### Post by mips on 2007-03-14
You have the option of both binaries & source.

---

### Post by ihavenoname on 2007-03-14
> **mips said:**
> You have the option of both binaries & source.

excellent, thank you!

---

### Post by angryfirelord on 2007-03-20
> **brucevangeorge said:**
> I also hear that linux needs to be emulated. Emulation = bottleneck from my experience.

All you have to do is type this in your /etc/rc.conf file
```
linux_enable="YES"
```

Most Linux binaries run as fast in BSD, so there's no bottlenecking involved.

---

### Post by ertrules22 on 2007-08-07
[FreeBSD]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/index.html")
[OpenBSD]("http://www.openbsd.org/faq/index.html")
[NetBSD]("http://www.netbsd.org/docs/#guides")
Here are a few FAQ's etc. If you want to have a looksie!
:lolflag:
personally I use FreeBSD (because of it's size and it's a little more popular, so has a larger community support team \\:D/

---

### Post by ihavenoname on 2007-08-11
yea I tried Freebsd and PCBsd I liked them. There is a lot to like about BSD OS's. However I ended up coming back to Linux because it has much better binary package support. One day I'll try it again though.

---

### Post by csimons on 2007-08-12
I've used FreeBSD more than any other variant, and as far as my experience goes it is the most well-supported, well-documented, and user-friendly variant.

Prepare for things to be installed where they /should/ be installed.  Things that belong in /usr/local/bin and /usr/local/etc will be there.

Also, since the ports tree management system compiles everything from scratch, programs might run slightly faster than precompiled packages built for a generic 386 architecture.  Not that you can't build from source on Linux obviously, but it's nice to have a skeletal structure of makefiles for nearly every package you could possibly want, all ready to build.

I'd recommend doing a pretty minimal install, and then building the packages you need.  If you want something that isn't installed, go to /usr/ports/category/appname and do "make install clean".  FreeBSD will compile and build the dependencies automatically.  So, for example, if you install only the bare essentials and need X windows, simply go to /usr/ports/net/gaim and run make, and all the X and GTK dependencies will be built, with no extra fluff.

Oh, one more.  In the terminal, if you hit [scroll lock] and then use the up and down arrows, you can scroll through the terminal history!  Spectacular!

If you want more info on configuring particular things, "Absolute BSD" from No Starch Press is an excellent book very well written, and one can read it entirely within three or four days because the writing style is so friendly and engaging.

---

### Post by ihavenoname on 2007-08-12
> **csimons said:**
> I've used FreeBSD more than any other variant, and as far as my experience goes it is the most well-supported, well-documented, and user-friendly variant.

Prepare for things to be installed where they /should/ be installed.  Things that belong in /usr/local/bin and /usr/local/etc will be there.

Also, since the ports tree management system compiles everything from scratch, programs might run slightly faster than precompiled packages built for a generic 386 architecture.  Not that you can't build from source on Linux obviously, but it's nice to have a skeletal structure of makefiles for nearly every package you could possibly want, all ready to build.

I'd recommend doing a pretty minimal install, and then building the packages you need.  If you want something that isn't installed, go to /usr/ports/category/appname and do "make install clean".  FreeBSD will compile and build the dependencies automatically.  So, for example, if you install only the bare essentials and need X windows, simply go to /usr/ports/net/gaim and run make, and all the X and GTK dependencies will be built, with no extra fluff.

Oh, one more.  In the terminal, if you hit [scroll lock] and then use the up and down arrows, you can scroll through the terminal history!  Spectacular!


Does the scroll lock trick not work on linux? 

My main "issue" with BSD is that everything is compiled from source. I would rather trade program running speed down so long as I get the programs I need quickly. Compiling is a pain. I think Arch Linux has the best BSD/Linux trade off by making compilation as easy as it is in BSD and also have fantastic binary package support.

---

### Post by Bachstelze on 2007-08-12
> **ihavenoname said:**
> My main "issue" with BSD is that everything is compiled from source.

Wrong. Both Free- and OpenBSD provide precompiled packages, and Open- recommends it as the preferred way of installing software. It actually works pretty much the same way as Apt does : *sudo pkg_add -vi gimp* and you have GIMP and all the dependencies.

---

### Post by ihavenoname on 2007-08-13
> **HymnToLife said:**
> Wrong. Both Free- and OpenBSD provide precompiled packages, and Open- recommends it as the preferred way of installing software. It actually works pretty much the same way as Apt does : *sudo pkg_add -vi gimp* and you have GIMP and all the dependencies.

Ok, let me clarify this. During my experiance with FREEBsd, I had a nightmare of a time upgrading from Xorg 6.9 to Xorg 7.2 because the packages where in a seperate repository. I had to manually satisfy those dependencys. Also, from what I understood from FreeBsd, compiling from source was best supported as binary package updates tended to have long intervals in between. Linux just has BETTER binary package support.

---

### Post by Bachstelze on 2007-08-13
> **ihavenoname said:**
> Also, from what I understood from FreeBsd, compiling from source was best supported as binary package updates tended to have long intervals in between. Linux just has BETTER binary package support.

That's very possible. Feel free to contribute and make binary packages :)

And different systems have differend philosophies. As I told you, OpenBSD's is to make binary packages and recommend it over compiling from source, and updates are no slower than in Ubuntu since OpenBSD also has a six-month release cycle.

---

### Post by jrusso2 on 2007-08-13
Tried FreeBSD, came back to Linux.  Linux makes the best desktop.

---

### Post by kellemes on 2007-08-13
> **jrusso2 said:**
> Tried FreeBSD, came back to Linux.  Linux makes the best desktop.

Well, if "Desktop" (whatever that may be) is what you find in GNU/Linux you've come home.. Although (as far as I know) BSD gives you most (if not all) the "Desktop" you get with GNU/Linux.
But there can be a million other reasons to base your choice of OS on..

---

### Post by ihavenoname on 2007-08-13
> **HymnToLife said:**
> That's very possible. Feel free to contribute and make binary packages :)

And different systems have differend philosophies. As I told you, OpenBSD's is to make binary packages and recommend it over compiling from source, and updates are no slower than in Ubuntu since OpenBSD also has a six-month release cycle.

I never tried OpenBSD, now I might. I would love to be able to contribute binary packages for Bsd as I prefer the BSD phiosphy (Sp?). However I don't know how and I don't have time currently. (Moving in, then Collage etc.). If  I get some free time I will definitly look in to OpenBsd, thanx for the hint. Though I think I'll go for something like Desktop BSD or w/e since it's based off of OpenBSd (or do you reccommed other wise?) BSD is the next step for me, but it's not yet time.

---

### Post by mips on 2007-08-14
> **ihavenoname said:**
> Though I think I'll go for something like Desktop BSD or w/e since it's based off of OpenBSd 

Desktop & PCBSD is based on FreeBSD, not OpenBSD.

---

### Post by ihavenoname on 2007-08-14
> **mips said:**
> Desktop & PCBSD is based on FreeBSD, not OpenBSD.
So whats based off OpenBsd? Anything? Oh well I'll just try the real deal.

---

### Post by kellemes on 2007-08-14
> **ihavenoname said:**
> So whats based off OpenBsd? Anything? Oh well I'll just try the real deal.

OliveBSD among maybe some others..

---

### Post by jrusso2 on 2007-08-15
> **kellemes said:**
> Well, if "Desktop" (whatever that may be) is what you find in GNU/Linux you've come home.. Although (as far as I know) BSD gives you most (if not all) the "Desktop" you get with GNU/Linux.
But there can be a million other reasons to base your choice of OS on..

Desktop as opposed to server.  BSD makes an awesome server where the limitations that are apparent on a desktop are not so much of a problem.

Somethings like flash support, and driver support, video and wireless support are not needed on a server.

Linux is plenty stable enough for desktop use, so the benefits of BSD's being so rugged are not as needed, and don't make up for its other shortcomings.

---

### Post by Bachstelze on 2007-08-15
Has it never occured to you that some people just have the will to learn about new OSes, even it they won't provide them all the bells and whistles Linux does ? What do you think you have to gain in posting all those rants ? The warm and fuzzy feeling that you convinced one user to stay in the right way and never go outside of it ?

I really don't understand people like you. You don't like the evil BSD on the desktop, fine. But don't discourage others who would like to try it. If it's as bad as you say, they will be back using the holy Linux in no time.

---

