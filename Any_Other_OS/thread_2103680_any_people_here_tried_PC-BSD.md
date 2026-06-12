---
title: "any people here tried PC-BSD?"
date: 2013-01-10
forum: Any Other OS
---

### Post by paradive on 2013-01-10
what were your impressions?

---

### Post by BBQdave on 2013-01-11
> **paradive said:**
> what were your impressions?

Awhile back I tried PC-BSD 8. Difficult to get all my hardware working - though that may not be an example over all of PC-BSD.

My very rough impression... Linux better supported and more developed than freeBSD, aka PC-BSD, in the desktop arena.

---

### Post by MoebusNet on 2013-01-13
Posting this from PC-BSD 9.1 64-bit running in VirtualBox on Ubuntu 12.04. PC-BSD seems to be making strides towards better desktop compatibility. Still some issues with hardware compatibility, so you may want to try a Live-USB image or install a VBox or VMware image unless you have a spare machine to try a bare metal install.

My VM in VBox still has some networking issues (just got networking going) but everything else so far is working as expected. Should be interesting to watch this continue to develop.

---

### Post by Dlambert on 2013-01-13
I've said this before, but I believe that bsd Will die out And eventually merge with linux.

---

### Post by sffvba[e0rt on 2013-01-14
> **Dlambert said:**
> I've said this before, but I believe that bsd Will die out And eventually merge with linux.

BSD on servers is alive and kicking and bringing out new and interesting things all the time.  On the desktop it might never be prominent.


404

---

### Post by trent.josephsen on 2013-01-14
Insofar as "it won't boot" can be considered an impression...

I liked FreeBSD though. Would have been great as a server OS; unfortunately, it didn't last long on my desktop.

---

### Post by Ashtonford on 2013-01-14
> **paradive said:**
> what were your impressions?

to many things dont work like touch pads etc on lap tops.  It may be ok on a desktop.

---

### Post by Famicommander on 2013-01-14
I have used it as one of my OSes (along with Xubuntu, Mint, Lubuntu, and Fedora) for the last few years.

It is very stable and very easy to use, but it lacks some hardware support (specifically for AMD video cards and laptops) and software support. It's very usable in a desktop setting with an Nvidia card, but I'm not sure I would recommend it over a more fully featured Linux install at this point. It doesn't offer much that *buntu, Mint, Fedora, Arch, Mageia, OpenSUSE, Sabayon, PCLinuxOS, Debian, or Slackware don't offer in a more mature form.

---

### Post by trent.josephsen on 2013-01-14
I wonder if anyone could comment (subjectively) on how it differs from the other BSDs? I'd be interested...

---

### Post by BBQdave on 2013-01-14
> **trent.josephsen said:**
> I wonder if anyone could comment (subjectively) on how it differs from the other BSDs? I'd be interested...

Though I am sure Unix folks would disagree, just as Linux folks disagree on the best Linux distro...

If you are going to check out Unix, than **freeBSD** is the lead branch - and thus **PC-BSD** is the most enriched desktop release of the Unix branches.

---

### Post by Famicommander on 2013-01-15
> **trent.josephsen said:**
> I wonder if anyone could comment (subjectively) on how it differs from the other BSDs? I'd be interested...
There are very few BSD operating systems which target desktop users; most like NetBSD, FreeBSD, and Openfly BSD are server/embedded market operating systems. You can certainly install desktop programs onto them, but they don't come with a GUI by default and are not for the unexperienced. 

PCBSD is by far the most user friendly distribution of BSD. You might also check out Debian GNU/kfreebsd (still in testing as far as I know but it's basically Debian with the freebsd kernel instead of the Linux kernel) or GhostBSD (much smaller scale project than the other two).

PCBSD is essentially freebsd with your choice of GUI and lot of changes to make it user friendly. But the underlying freebsd system and functionality are still there.

---

### Post by trent.josephsen on 2013-01-15
I've used FreeBSD and NetBSD before; I'm more interested in the package management aspect and the specific changes PC-BSD makes to the installation process and desktop environment. Does it feel more polished, professional, responsive, idiotproof, etc.?

---

### Post by Famicommander on 2013-01-15
> **trent.josephsen said:**
> I've used FreeBSD and NetBSD before; I'm more interested in the package management aspect and the specific changes PC-BSD makes to the installation process and desktop environment. Does it feel more polished, professional, responsive, idiotproof, etc.?

You still have access to the FreeBSD Ports tree, but PC-BSD has its own package management program called AppCafe (Similar to the Ubuntu Software Center). AppCafe uses a file format called .pbi (push button installer), which is essentially equivalent to a .exe in Windows or a .deb in Debian systems.

It is definitely more idiot proof than a raw FreeBSD install. It comes with your choice of GUI (KDE by default) and it includes many graphical applications for configurations and settings, so you really shouldn't have to jump into the command line unless you want to. 

It definitely has polish. In fact, PC-BSD's implementation of KDE is probably the only time I have had a KDE desktop not give me constant head aches from refusing to behave the way I wanted it to.

It's a stable, fast, solid, and very easy to use operating system. As I said above, its major drawbacks are AMD video card support and some laptop specific issues. There is also a smaller selection of software than you might find in a major Linux distro like Ubuntu or Fedora, but the newest version of PC-BSD does allow you to run Debian programs from a jail (requires configuration).

I am by no means an expert, so if you're still interested I would recommend the PC-BSD forums:
[http://forums.pcbsd.org/](http://forums.pcbsd.org/)

---

### Post by trent.josephsen on 2013-01-15
Nifty. Thanks for that concise description; I hope it helped OP some too.

---

### Post by TeamRocket1233c on 2013-01-27
I tried GhostBSD and I'm a pretty big fan of it, and I'm considering trying DragonflyBSD, but hadn't tried PC-BSD yet.

---

### Post by dh04000 on 2013-01-28
IMO, PC-BSD has the best KDE deflaut setup and work flow of any KDE set up, even in linux land.

---

### Post by oscarivera9 on 2013-01-28
Like most people have said, I've tried PC-BSD9 and had problems with some of the hardware.  When I installed it as a virtual OS with VirtualBox, everything was fine and it ran pretty smooth (for a virtual machine).  The version that I installed in VirtualBox used the Gnome 2.xx DE but I know that there are other desktop environments available as well.  After using for a few weeks I then decided to try and install it on an actual physical HDD and I encountered a few problems.  My PC has pretty new components (I built it) and that's why I believe there were compatibility problems.  Ubuntu, however, has no problems whatsoever with my hardware; in fact, I don't use any proprietary drivers (not even for my ATI/Radeon graphics card).
If I were you I would try to see if you can get a Live USB (or Live CD if you can find one) to test for compatibility with your PC.  At the PC-BSD downloads page you will see 4 USB options (2 for 32-bit and 2 for 64-bit) and all of these should be able to be used as a Live USB so you can try it out.
[http://www.pcbsd.org/en/download.html](http://www.pcbsd.org/en/download.html)

---

