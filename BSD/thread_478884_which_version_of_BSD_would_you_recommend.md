---
title: "which version of BSD would you recommend?"
date: 2007-06-19
forum: BSD
---

### Post by bc135 on 2007-06-19
OpenBSD, netBSD, or FreeBSD?

I'm specifically asking about these versions because I want to run them virtually using VirtualBox, just to play around with BSD a bit. Here are my specs (laptop):

Toshiba Satellite A70
Pentium 4-M Prescott @ 3.06GHz
1.5GB DDR SDRAM
120GB HDD spinning @ 5400RPM
128MB Radeon 9100 IGP
Atheros "Super G" AR5004G mini-PCI wireless card


Any input is appreciated.

---

### Post by OrbJinzo on 2007-06-19
In my exepernice with BSD FreeBSD seems to have the best hardware support.

---

### Post by Bachstelze on 2007-06-20
Since you just want to try them out virtualized, why not try them all ? ;) Open is my recommendation but please don't take my word for it and also try at least Free. Both of them make very robust desktop systems (haven't tried Net much)

---

### Post by bc135 on 2007-06-20
I probably will end up using either Free or Open, but if one of them has a graphical installer, I'll go for it.

---

### Post by Bachstelze on 2007-06-20
If you like a graphical installer, you might want to try PC-BSD or DEsktopBSD - which are basically FreeBSD with all the glitter added to it. I personnally don't like them, as I find them way too bloated, but it's all up to you.

---

### Post by mips on 2007-06-20
> **bc135 said:**
> I probably will end up using either Free or Open, but if one of them has a graphical installer, I'll go for it.

Do it the hard way and go OpenBSD. If you want the easy way then go PCBSD or DesktopBSD.

---

### Post by iqag1060 on 2007-06-20
OpenBSD doesn't have a graphical installer, but installation is remarkably easy. If you run it in Qemu, make sure to disable kqemu. In my opinion, the choice really depends on what you plan to use them for. OpenBSD policy sort of frowns on installing software that's not in the ports tree - which does not always include the latest version. Which is not to say you can't do it, it's just not the OpenBSD way. Try them all, learn their idiosyncrasies, then come back to Ubuntu.

---

### Post by bc135 on 2007-06-20
I'd prefer the easier installation method, unfortunately VirtualBox has limited support for FreeBSD as it is, much less support for PC or Desktop BSD. If I install PC/Desktop BSD, will it automatically create a multi-boot setup similar to Ubuntu's (I have XP and Ubuntu)?

---

### Post by Bachstelze on 2007-06-20
FreeBSD does nothing "automatically", you do it yourself.

---

### Post by theonlyrealperson on 2007-06-23
I'm running FreeBSD on my laptop, and it's become my preferred OS. This site really, really helped me get it up and running:

[http://www.openaddict.com/howtos.html]("http://www.openaddict.com/howtos.html") 

Follow the beginning, and then follow the link to the workstation and follow those, and you have a rock-solid FreeBSD base.

One note, at the end of the workstation it tells you to install kde via ports. That took two days on my IBM T42p laptop. Not a big deal, but a lighter way to go is either install kde via packages (if you don't mind a slightly older version) or just install the base system, if you don't mind not having "kdeedu" and such. To install the base system, just install qt, arts, kdelibs, kdebase, (any of the other kde packages: games, kdeedu, kdedevelop, etc), then lastly kdeaddons in that order.

---

### Post by Bachstelze on 2007-06-23
Actually, just installing *kdebase* is enough, it will also install all the dependencies ;) You can then install all the other KDE packages in any order you wish, or not install them at all.

---

### Post by theonlyrealperson on 2007-06-24
That's a good thing to know. I was only going off of what a website said. I haven't gotten around to uninstalling and reinstall kde yet. (I wouldn't mind opening up some of that disk space though!)

---

### Post by Enverex on 2007-06-24
> **theonlyrealperson said:**
> I'm running FreeBSD on my laptop, and it's become my preferred OS. This site really, really helped me get it up and running:

[http://www.openaddict.com/howtos.html]("http://www.openaddict.com/howtos.html") 

Follow the beginning, and then follow the link to the workstation and follow those, and you have a rock-solid FreeBSD base.

One note, at the end of the workstation it tells you to install kde via ports. That took two days on my IBM T42p laptop. Not a big deal, but a lighter way to go is either install kde via packages (if you don't mind a slightly older version) or just install the base system, if you don't mind not having "kdeedu" and such. To install the base system, just install qt, arts, kdelibs, kdebase, (any of the other kde packages: games, kdeedu, kdedevelop, etc), then lastly kdeaddons in that order.

I have to ask, why would someone want to use FreeBSD (or just BSD) over say Debian (or Linux in general)? I've always wondered that. I always thought BSD was just a more hardened kernel which is useful for servers, but as a desktop it's just basically Linux but unable to run all Linux software...

---

### Post by Bachstelze on 2007-06-24
Why BSD is better than Linux ? It is a mostly unanswered question, which is subject to countless (and often useless) religious debates - and is often considered a troll. There is no better, only different. The best OS for you is alwas the one you like best.

---

### Post by theonlyrealperson on 2007-06-24
Well, it started as a learning experience. I've only been Windows "Free" since February. I first tried Ubuntu Dapper, and I've been hooked on everything-Not-M$ ever since. I quickly turned into a distro-hopper for a while, and I wanted to try a BSD.

I like the speed of FreeBSD, and I like the documentation. In my opinion, FreeBSD is very, very well documented and easier for me to work with and fix. I've had far more success with rebuilding a kernel in FreeBSD than I have had with Slackware. I've also had better luck with hardware in FreeBSD than Slackware.

When it comes down to it, I like it and it works for me. ;)

---

### Post by ropers on 2007-12-15
> **Enverex said:**
> I have to ask, why would someone want to use FreeBSD (or just BSD) over say Debian (or Linux in general)? I've always wondered that. I always thought BSD was just a more hardened kernel which is useful for servers, but as a desktop it's just basically Linux but unable to run all Linux software...

OpenBSD can emulate Linux and FreeBSD. I don't know about the others. That said, the way you're asking this makes me think that OpenBSD probably isn't for you. OpenBSD does not try to convert people, get more users than other OSes or go for market share. OpenBSD does not "want you". You have to want OpenBSD. That said, there are good reasons why you might do so. Google and the OpenBSD website would be a good start.

---

