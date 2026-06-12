---
title: "FreeBSD as a Desktop OS?"
date: 2013-08-16
forum: Any Other OS
---

### Post by mamamia88 on 2013-08-16
So I bought a cheap desktop on ebay to use as an htpc instead of converting mkv all the time.  But turns out my ps3 has much higher video quality via hdmi then the pc via vga so i decided to just use it to exeriment on.  So I installed freebsd which i've always been curious of.  Took all of 10 minutes to finish the base install which was impressive.  But when i was done i got some error due to a incomplete hostname. It wanted a hostname like a webserver but for desktop use you don't need that.  That's hassle number one which could be fixed if i cared enough.  Hassle number 2 is that download speeds for packages aren't nearly as fast as on debian or arch.  I'm talking 100kbps.  So even to install nano was taking forever.    I just gave up and slapped debian on it.  It's so much simpler for desktop use and you get the same result.  So my question is have you ever run freebsd as a desktop and what were your results like?

---

### Post by tgalati4 on 2013-08-16
I run freenas as a NAS--network attached storage.  It's slim and generally fast, but BSD in general has more limited hardware support than linux.  It's possible that your network card (or wireless) was not running well with the BSD driver.  A google search of BSD with your model of network card might give some clues.  Debian can be slim as well.

---

### Post by mamamia88 on 2013-08-16
I'm not too worried about slim.   I'm just saying that my initial impressions is that it would probably be great for stuff that you want to setup and forget about like a nas system but for something you interact with on a day to day basis it's probably not the best choice.  It could very well be the ethernet driver causing the slowdown.

---

### Post by BBQdave on 2013-08-16
[**PC-BSD**]("http://www.pcbsd.org/") might be your best shot at the desktop :)

At the risk of *poking the bear*, I think *any*BSD lost to Linux long ago - with the Unix lawsuits of the early 90's, Unix development froze for a few years. Folks looked to Linux, and from there, the rest is history with GNU/Linux.

*Any*BSD has never matched the popularity and number of devs that Linux has :)

---

### Post by mamamia88 on 2013-08-16
> **BBQdave said:**
> [**PC-BSD**]("http://www.pcbsd.org/") might be your best shot at the desktop :)

At the risk of *poking the bear*, I think *any*BSD lost to Linux long ago - with the Unix lawsuits of the early 90's, Unix development froze for a few years. Folks looked to Linux, and from there, the rest is history with GNU/Linux.

*Any*BSD has never matched the popularity and number of devs that Linux has :)

which is kinda what got me curious about it.  if i found out that dinosaurs where still alive in part of the world i'd have to go  visit that too.   just seems weird to go through all that work to end up with a desktop with less software support for stuff like dropbox and chrome when i can start the debian install,take a shower while it finishes, reboot system, mark all apps i want installed in synaptic, watch a tv show and let it download and install, and have a pretty much working system.  Sure advanced stuff like setting up my vpn might take a little extra learning but for the most part it's that simple.

---

### Post by tgalati4 on 2013-08-16
It becomes clear what the showstoppers are when using BSD derivatives.  As soon as you find a service that you can't use, you tend to look elsewhere.  But I would go see the Dinosaurs.

---

### Post by Kenta_S. on 2013-08-16
Most of the "problems" you listed were due to lack of knowledge on your part and are not actually problems. The requirement for a fully-qualified hostname means you should use "myname.local" or something instead of just "myname" - Linux has a bad habit of not adhering to standards, so you don't need this on Ubuntu.
In FreeBSD, we use the Ports collection to install software. Packages (pkg_add/pkgng) are discouraged. You can change the mirror you download either of them from in /etc/make.conf. All of this (and more) is outlined in the handbook: [http://freebsd.org/handbook](http://freebsd.org/handbook)

I recommend giving it another try once you've read through the basics. See also:
[http://www.over-yonder.net/~fullermd/rants/bsd4linux/01](http://www.over-yonder.net/~fullermd/rants/bsd4linux/01)

---

### Post by buzzingrobot on 2013-08-16
I ran FreeBSD as a desktop several years ago with no problems.  But, frankly, with no real advantage over a good Linux desktop. You spend almost all your time with a desktop interacting with applications that are the same on both platforms.

FreeBSD doesn't "work" like Linux.  Different admin tools and procedures, different concept of how software should be delivered and installed. So, a Linux user will face a learning curve.

It has a long and storied history, which is well worth reading about.

---

### Post by mamamia88 on 2013-08-16
> **buzzingrobot said:**
> I ran FreeBSD as a desktop several years ago with no problems.  But, frankly, with no real advantage over a good Linux desktop. You spend almost all your time with a desktop interacting with applications that are the same on both platforms.

FreeBSD doesn't "work" like Linux.  Different admin tools and procedures, different concept of how software should be delivered and installed. So, a Linux user will face a learning curve.

It has a long and storied history, which is well worth reading about.

So can you run all linux software or just most of it?  I want to give it a try again but i need to do my research to make sure i know what i'm getting into.  Today curiousity just got the better of me and i had nothing to lose so figured Id go for it.

---

### Post by mamamia88 on 2013-08-17
> **Kenta_S. said:**
> Most of the "problems" you listed were due to lack of knowledge on your part and are not actually problems. The requirement for a fully-qualified hostname means you should use "myname.local" or something instead of just "myname" - Linux has a bad habit of not adhering to standards, so you don't need this on Ubuntu.
In FreeBSD, we use the Ports collection to install software. Packages (pkg_add/pkgng) are discouraged. You can change the mirror you download either of them from in /etc/make.conf. All of this (and more) is outlined in the handbook: [http://freebsd.org/handbook](http://freebsd.org/handbook)

I recommend giving it another try once you've read through the basics. See also:
[http://www.over-yonder.net/~fullermd/rants/bsd4linux/01](http://www.over-yonder.net/~fullermd/rants/bsd4linux/01)

yeah i read the handbook which says the hostname should be a fully qualified hostname and says absolutely nothing about what the heck that is.  like everybody reading has an idea.  if it was the arch wiki i'd be able to click it and it would take me to another article actually explaining it.   so i did cat /etc/hosts on my arch machine so i get localhost.localdomain.   so for a freebsd system would a fully qualified name be something like whatiwantmyhostnametobe.localhost.localdomain if i don't have a webserver?

---

### Post by buzzingrobot on 2013-08-17
> **mamamia88 said:**
> So can you run all linux software or just most of it?  I want to give it a try again but i need to do my research to make sure i know what i'm getting into.  Today curiousity just got the better of me and i had nothing to lose so figured Id go for it.

I suspect a look around freebsd.org would uncover a roster of apps someplace. Linux apps need to be ported -- different OS, different packaging methods, etc. -- but what you're looking for is probably available. "All" Linux software includes things like Unity and many distro-specific tools that wouldn't make sense on FreeBSD.   Only way to know for sure is to check.

I don't see any real advantage for a mainstream user in using FreeBSD as a desktop over Linux, frankly.  It's a different road that gets you to the same place.

---

### Post by mamamia88 on 2013-08-17
So i set it up again and just have a cli.   I can tell that getting a working gui will be a pain in the ass.  I canceled out of installing xorg from ports  because it was taking too long and pkg_add -r kept fetching packages and telling me they were already installed.  Wouldn't it be nice not to waist my bandwith and check if it's installed prior to downloading?  I very much prefer the way that yaourt/pacman work on arch

---

### Post by RichardET on 2013-08-17
I have an old Sun Blade 100, which is a sparc iie processor, 2 gig of ram, and (2) 15 gig IDE drives, circa 2001.  I used to run Solaris 9 on it, but have found the best BSD for it is OpenBSD and i have the current release 5.3 64 bit sparc installed.  The nice thing about OpenBSD is that X comes with it, unlike FreeBSD.  Also, the developers for OpenBSD are really top notch and I think FreeBSD is second rate compared to OpenBSD.  So I would use either OpenBSD for Intel arch or PC-BSD.

---

### Post by kevdog on 2013-08-18
I've always wanted to try a BSD derivative, but the more logical side of me says "why"?  Yes I'd learn a lot and probably appreciate a lot of things, but other than for educational purposes, I can't come up with any real benefit a BSD install would give me over a Linux install.

---

### Post by Habitual on 2013-08-19
> **mamamia88 said:**
> So can you run all linux software or just most  of it?  I want to give it a try again but i need to do my research to  make sure i know what i'm getting into.  Today curiousity just got the  better of me and i had nothing to lose so figured Id go for it.

If I may interject my observation here.
When I installed FreeBSD (9.1?)to my desktop workstation recently, I had severe withdrawals when some of my favorite "doo-dads" wouldn't install, such as,

[LIST]
[*]ElastiFox-ec2tag for my work with Amazon entities. - ***Show stopper***. (I work with AWS all day, every day).
[*]FireTray for Thunderbird (new message count notification) - Annoying but no bid deal.
[*]Persistant ntfs(-3g) for WD 3T USB drive via /etc/fstab which I overcame.
[/LIST]

I am a very experienced and technically proficient Systems Administrator.
So my experience has been "some" Linux software will run.
Now this all depends, I guess on the term "software".

Any derivative may also show similar annoyances.
I'd suggest keeping a Linux system around and/or dual-boot Linux with FreeBSD "just in case".

Again, this is just my personal perspective on my experience with Linux Software on FreeBSD.

Other than that, it is a top-notch Distribution.

---

### Post by mamamia88 on 2013-08-19
> **kevdog said:**
> I've always wanted to try a BSD derivative, but the more logical side of me says "why"?  Yes I'd learn a lot and probably appreciate a lot of things, but other than for educational purposes, I can't come up with any real benefit a BSD install would give me over a Linux install.

I'd actually say that installing freebsd just the base system is super super easy.   And for a server I'm sure it would be a great choice. Getting it up and running as a desktop is a complete other story. You already chose to limit yourself slightly running linux i don't see why you'd want to limit yourself even more with freebsd. No native dropbox or chrome comes to mind.  In contrast on arch after the base install to get to a desktop all i had to do was 
```
pacman -S xorg xf86-video-intel xfce4 xfce4-goodies
cd /etc/skel
cp .xinitrc /home/username
remove the # from in front of xfce line in .xinitrcfile
systemctl enable slim.service
reboot
```
All I had to know was the make and model of the video card and no compiling was needed so it was super quick.  Once you get the hang of it arch is a perfect compromise between customizability and ease of use.

---

### Post by RichardET on 2013-08-19
I have tried freebsd and openbsd and pcbsd.  The two former on an old sun blade 100, which is sparc 64bit and the latter as a Intel based VM.  OpenBSD is much better than freebsd, and I think PCBSD may be the best for Intel based equipment.  But I have to warn you that Theo & company on openbsd can be quite nasty towards linux people.  Somehow the Torvalds- De Raadt fight is unresolved.

---

