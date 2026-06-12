---
title: "should I try a flavor of BSD ?"
date: 2007-03-11
forum: BSD
---

### Post by billdotson on 2007-03-11
I was wondering is trying a various flavor of BSD worth my time?  I have seen FreeBSD, OpenBSD, NetBSD, etc. and I was wondering if any of them are worth trying.

---

### Post by bukwirm on 2007-03-11
If you have the time and are interested, sure.
Make sure you read the manuals, though - there are some differences between the various BSD flavors and Linux.

---

### Post by billdotson on 2007-03-11
so what is the *best* version of BSD?

---

### Post by 23meg on 2007-03-12
It's...

* tosses coin *

...NetBSD. 

Because I say so. It's worth your time, and it's worth trying. It's universally the best version of BSD, for everyone, without exceptions. It's worth trying for everyone, and it's worth everyone's time, even of those who give no hints of what they consider to be "good", or "worth trying", and expect definitive answers or useful advice.

Try it and you'll see.

---

### Post by kvonb on 2007-03-12
It depends what you want to use *BSD for.  If you want to use it as a server, or for writing *BSD apps, and you are either very good with solving software problems, enjoy compiling EVERY app from source, or just like a challenge, then sure go for NetBSD, FreeBSD et al.

If you want a desktop system, with lots of easily installed packages, go straight to PCBSD.

[www.pcbsd.org](www.pcbsd.org)

In my opinion it is amazing, very well put together, tons of packages ready made, video drivers available, and rock solid, (although that is a trait of all the BSDs).  They have a well organised, simple web-site with pages of categorised applications which are more like the Windows one file, one click install method, no messing around with compiling, dependencies etc'.

If I ever had to drop Ubuntu, PCBSD would be my first port of call :)

---

### Post by handy on 2007-03-13
I use Ubuntu for gaming & PC-BSD for everything else!

---

### Post by wiseleader on 2007-05-06
> **handy said:**
> I use Ubuntu for gaming & PC-BSD for everything else!

I'd like to try BSD, heard that it's more stable and linux applications are workings on bsd o/s. But worrying about hardware drivers.

I was a Window user 8 years ago, Linux distributions are stable enough for me, however, if I can find a more stable and heavy-loadable platform (nearly identical to linux in operation), why not take a trial ?

---

### Post by Sef on 2007-05-07
> If you want a desktop system, with lots of easily installed packages, go straight to PCBSD.

[www.pcbsd.org](www.pcbsd.org)


Thank you for that info.  I m having a problem with Feisty on one of my computers, and so I hope this will work better on it if I can't get Feisty to run right.

---

### Post by RAV TUX on 2007-05-08
> **kvonb said:**
> [www.pcbsd.org]("http://www.pcbsd.org")  

**[PC-BSD]("http://www.pcbsd.org/")** is simply awesome also [**[B]DesktopBSD**[/B]]("http://www.desktopbsd.net/") is great also.

I used to dual boot **[PC-BSD]("http://www.pcbsd.org/") **with Ubuntu for about a year[B].
[/B]

---

### Post by tgalati4 on 2007-05-08
Don't forget Tiger.  It's the best commercial implementation of BSD.  It's really worth the $129 they charge for it.  Of course you need to buy mac hardware.

The music player is pretty good on Tiger.

---

### Post by beartard on 2007-05-14
If you're going to try a customized, desktop-oriented install of a BSD, go for DesktopBSD over PC-BSD.  It is the "purer" of the two.  dBSD gives you a customized install of FreeBSD with everything set up and configured like you'd like it, using a nice, KDE desktop.  On top of the FreeBSD base are the DesktopBSD tools, such as a synaptic-like package manager and a network manager.  Since it uses the standard FreeBSD base, you can draw on support from that entire community.  PC-BSD uses FreeBSD as a base as well, but it departs from "tradition" and uses its own packaging system.

But don't expect what you get from Ubuntu.  BSD, because of its stability, is way behind Linux in some areas.  You'd never see xorg 7.2 with compiz and beryl because, unlike the wild Linux-ites, the BSD group knows their system is stable...and they want it to stay that way.

Also, BSDs use OSS, not ALSA.  I think Linux should still use OSS, too, but that's just my opinion.  Apps that require ALSA, therefore, made themselves Linux-only.  If you have anything along those lines that's essential (like music notation and MIDI for me) Linux might be better to stick with.

It is true that BSD can run some Linux binaries (like java, adobe reader, flash, etc.) but this comes at the expense of installing a significant portion of a Gentoo system under a /compat directory under BSD.  Is it worth it?  ;-)

---

### Post by tchoklat on 2007-06-02
I would like to put PC-BSD on an unused partition on my multi-boot system. Can I get assistance as follows?
 
I install it to an unused partition.
To continue to use my exusiting Ubuntu Grub what do I do?
Do I chainload or configsys or what?
 

tchoklat

---

### Post by bAdSkAtEr on 2007-06-12
I appreciate the non-warlike responses to a question such as "what is the best BSD?" :-)

I have used OpenBSD and FreeBSD, and I prefer each for different reasons:

Overall, OpenBSD is my favourite.  Very clean basic installation.  Supposedly (one of) the most secure OSs available.  Sure, that is up to debate, but OpenBSD continues to be the OS of choice for many folks making edge devices and other machines which sit at the periphery of a network.  Fast, for most applications, and crazy stable.  OpenBSD, so far, is steadfast in keeping anything which is non-Free out of their system (Google terms such as "OpenBSD", "wifi", "blob")  I use it as a firewall/gateway, and as a Web server (Apache, MySQL, PHP, Perl, that kind of thing) and also email server.  MySQL performance for sizeable (is that a word?) databases is on the poorer side in OpenBSD, though for the kind of data I keep it is fine.  Several clients, however, need more juice to run MySQL, which brings me to...

FreeBSD.  Generally, FreeBSD is a bit faster than OpenBSD in many areas.  Certainly MySQL performance is much better under FreeBSD than OpenBSD -- even approaching that of a good Linux MySQL server.  In a perfect world, I would have Web and possibly email services running on OpenBSD, and database services running behind on FreeBSD (or Linux, though I prefer BSD for production servers).  FreeBSD is often considered to be (one of) the most stable of OSs.

I think someone mentioned this before, but with the various BSDs, think stability and maturity rather than latest and greatest.  That being said, I *do* like my gadgets, bells, and whistles on my desktop, so I tend to use Linux there (at this time, Ubuntu 7.04).

---

### Post by ertrules22 on 2007-08-07
I use FreeBSD for one reason only.  Ubuntu is too large for one of my laptops.  If you have an old laptop with less than 512 or 248 megs of ram, than I would reccommend FreeBSD (or another Flavor).  It has the same GUI feel for the most part as Ubuntu, but a much different terminal and kernel design.  Also, there is a lot more internal file editing to get it to work how you want (with a GUI) at the beginning.  I do like the way they do installation though.  You put in one disk to install FreeBSD, and another to choose from all the ports that are available.  Than you choose which ports/packages you want.
I would rather run Ubuntu, but FreeBSD is fun to play around with, and is perfect for an old and/or slow machine.
(like mine) :lolflag:

---

### Post by SlCKB0Y on 2007-08-17
[QUOTE=beartard;2656106You'd never see xorg 7.2 with compiz and beryl because, unlike the wild Linux-ites, the BSD group knows their system is stable...and they want it to stay that way.

It is true that BSD can run some Linux binaries (like java, adobe reader, flash, etc.) but this comes at the expense of installing a significant portion of a Gentoo system under a /compat directory under BSD.  Is it worth it?  ;-)[/QUOTE]

I dont know where to start with this post. I was running FreeBSD in January 2007. I was running xorg 7.2 and Beryl. So you are WRONG! Now xorg 7.2 is in ports, which make installing it even easier than when I used it.

Installing a small linux compat layer to be able to run a good proportion of linux binaries......yea ...a total waste of time.

---

### Post by Bachstelze on 2007-08-17
> **SlCKB0Y said:**
> Installing a small linux compat layer to be able to run a good proportion of linux binaries......yea ...a total waste of time.

I disagee here. It is a good, low-hassle way to run some Linux programs that are distributed in binary form without recompiling (games like OpenArena or NeverWinter Nights for example).

EDIT : Or was it ironic ?

---

### Post by beartard on 2007-08-17
> **SlCKB0Y said:**
> I dont know where to start with this post. I was running FreeBSD in January 2007. I was running xorg 7.2 and Beryl. So you are WRONG! Now xorg 7.2 is in ports, which make installing it even easier than when I used it.

Installing a small linux compat layer to be able to run a good proportion of linux binaries......yea ...a total waste of time.

If I'm wrong, I don't mind admitting it.  I still don't think you were using an xorg 7.2 port in January.  The point I was making is that Linux is quickly moving along with the bleeding-edge eye-candy stuff that causes endless headaches and makes the system as stable as George Bush.  The BSD variants don't include such nonsense officially until it's been tested and is working with very few flaws.  The xorg bit was just by way of example.

---

### Post by beartard on 2007-08-17
> **HymnToLife said:**
> I disagee here. It is a good, low-hassle way to run some Linux programs that are distributed in binary form without recompiling (games like OpenArena or NeverWinter Nights for example).

I agree it's low-hassle.  I see it as a concession on the part of the BSD world.  I never use it on my BSD systems, almost for ideological reasons, if that makes any sense.  I'm an operating-system racist:  I like my computers pure.  :)

---

### Post by SunnyRabbiera on 2007-08-17
I have heard a lot of good things about the newest PCBSD, and I myself have debated on trying it

---

### Post by ErusGuleilmus on 2007-08-17
You should go with PC-BSD. I actaully just downloaded it today and am running it as a virtual machine in Ubuntu. It is really nice.

---

### Post by beartard on 2007-08-19
> **ErusGuleilmus said:**
> You should go with PC-BSD. I actaully just downloaded it today and am running it as a virtual machine in Ubuntu. It is really nice.

If you're going to do that, might as well use BSD with the debian package manager.  ;-)

I like the ports system (it's the main selling point for BSD) and PC-BSD bends over backwards to get around it.

---

### Post by Bachstelze on 2007-08-19
> **beartard said:**
> If you're going to do that, might as well use BSD with the debian package manager.  ;-)

You mean something like [this](http://www.us.debian.org/ports/kfreebsd-gnu/) ? ;)

---

### Post by beartard on 2007-08-20
Exactly  :)

> **HymnToLife said:**
> You mean something like [this]("http://www.us.debian.org/ports/kfreebsd-gnu/") ? ;)

---

### Post by angryfirelord on 2007-08-20
Unfortunately, kFreeBSD is still using FreeBSD 5.5, which doesn't work with my wireless card.

So far, I've been enjoying PC-BSD 1.4 beta 1!

---

### Post by beartard on 2007-08-20
Whatever works for you is always best.  I know the feeling.  The only reason I'm running Linux on my main computer is because it has /dev/sequencer support for MIDI recording.  Also, Rosegarden only supports ALSA, unfortunately.  So I'm stuck, too.  ;-)

---

### Post by Coyote21 on 2007-09-20
> **billdotson said:**
> so what is the *best* version of BSD?

There is NO best version of BSD, it really depends of what you wanna do... If you want an secure system, then you should take OpenBSD, if you want an fast system, that is on the "bleeding edge" just like Linux, you should try FreeBSD. I've once tested FreeBSD in an virtual machine and liked him very much, it's the best option if you already know, something of Linux.

---

### Post by Bachstelze on 2007-09-20
> **Coyote21 said:**
> There is NO best version of BSD, it really depends of what you wanna do... If you want an secure system, then you should take OpenBSD, if you want an fast system, that is on the "bleeding edge" just like Linux, you should try FreeBSD.

And if you want to run it on your toaster, take NetBSD :D

---

### Post by Arwen on 2007-09-23
Wish me luck please,I'm downloading PCBSD to install it in my AMD Turion 64 laptop.I hope I won't get a wrong architecture error again just like when I tried to install NetBSD(i386) and I won't mess up bootmanager again :-P

---

### Post by SlCKB0Y on 2007-09-23
> **beartard said:**
> If I'm wrong, I don't mind admitting it.  I still don't think you were using an xorg 7.2 port in January.  

Nah it wasnt a port. I downloaded it through GIT and compiled it.

---

### Post by oomingmak on 2007-09-26
> **SunnyRabbiera said:**
> I have heard a lot of good things about the newest PCBSD, and I myself have debated on trying it
Out of curiosity, I decided to try out BSD some time ago.

I've tried the last 2 versions of PC-BSD (v1.3 back in Spring and v1.4 a couple of days ago). Neither of them would complete the install process on my machine (despite repeated attempts with freshly burned discs). They both kept crashing halfway through the install.

Every other OS I've tried (many different Linux distros, OpenSolaris, Windows etc.) all installed fine.

However, for some reason DesktopBSD installed perfectly fine, without any problems whatsoever (despite it also being based off FreeBSD).

---

### Post by Eddie Wilson on 2007-09-28
If you try a BSD distro try PCBSD 1.4 I've also used 1.3 and 1.4 is a top notch os. I've had no problems with it at all. Just be sure to get your partitions correct.
Eddie

---

### Post by Beau D. on 2007-09-30
Shouldn't be too hard to do. IIRC PCbsd just make a swap partition and a big lump / then applies its magic. Follow the guided installand your in the free and clear. 

Beau D.

---

### Post by maybeway36 on 2007-10-01
If you need to use NDIS drivers for wireless, make sure you install the source from CD#2.

---

### Post by ramjet_1953 on 2007-10-08
I have found the new release of PCBSD very good for my particular hardware config. The latest version is 1.4 and they have improved hardware detection dramatically.

I found the distrowatch download much faster than the PCBSD site.

Regards,
Roger :cool:

---

### Post by motang on 2007-10-15
> **billdotson said:**
> I was wondering is trying a various flavor of BSD worth my time?  I have seen FreeBSD, OpenBSD, NetBSD, etc. and I was wondering if any of them are worth trying.
If you have a spare machine or the hard drive space then why not?  Although I would suggest something like [PC-BSD]("http://www.pcbsd.org").  :)

---

### Post by TheS0urce1969 on 2007-10-30
PCBSD uses PBI which uses more space than using ports.  You can use the ports package on PCBSD but it is not recommended mixing the two.
I don't understand the need for pbi, how hard is it to type "make clean install or pkg_add"?  Desktopbsd uses GUI port manager which is very nice.  Desktopbsd has a live cd since 1.6 I believe, and Freesbie is a only a live cd.

Btw you can install binaries or compile from source either way it is very easy.  I only usually install for source when I have to.

---

### Post by maybeway36 on 2007-10-31
How do you set up PC-BSD so pkg_add works?

---

### Post by breakdaze on 2008-02-17
I have just set up and installed OpenBSD on an old computer with an AMD K6-2 CPU, a super socket 7 VIA chipset motherboard, an ATI Radeon 9200 SE VGA card, a Netgear 10/100 Ethernet LAN card, and an old 20Gb HDD.

I must say I am very impressed.  I am impressed at the excellent documentation, both on the OpenBSD web site, and the man pages loaded with the man page package at install.

The web site has an excellent FAQ that walked me through Installation.  After installing, I read the afterboot man page and did a few minor tweaks.  Finally, I used Google to look up my VGA card and monitor specs and configured X windows, once again using the excellent FAQ on the web site.

OpenBSD has a page that enumerates supported hardware and chips, so if you are running Linux, execute the command that enumerates your hardware (pciide?) and check it against the list.

With Ubuntu, I had trouble finding out how to make X windows fill my entire wide screen monitor with my old VGA card.  It wasn't easy to find an answer using the man pages, forum, or wiki.  But using the FAQ on the OpenBSD site I realized how to create a fresh xorg.conf and then exactly how to edit it.

The manual pages also are very good at referencing other man pages, and especially good at explaining what files to edit for configuration or tweaking.

However, OpenBSD isn't for people who want to run any drivers that have proprietary source code, or source code not available to the public.  The reason is the developers don't want to deal with code they cannot fix, test, or trust to be secure.

In short, my install went very smoothly, but it would have been somewhat of a pain if I had picked a dual-boot system.

I would say it has excellent hardware support, but you may have to unplug and plug an optical USB mouse in to get it working, however this may be a symptom of my old motherboard's chipset with the USB 1.1 by VIA.

Finally, if you would like to learn "real" Unix steeped in tradition, with roots at Berkeley at Bell Labs, try a BSD flavor.

However, if you want to utilize the fancier aspects of your VGA card, or want to run a lot of other fancy software, perhaps it is not for you.

I personally think administering a system from the command line, reading manual pages, and perhaps printed books really helps with overall use and tweaking of any *NIX type OS in the long run.

For example, the hier command on OpenBSD told me things about the directory structure I never understood before.

YMMV

---

