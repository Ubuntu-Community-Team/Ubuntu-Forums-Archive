---
title: "A question about PCBSD"
date: 2007-04-14
forum: BSD
---

### Post by darksong on 2007-04-14
Can anyone tell me if there is another way to install software through it except PBI's? On the forums i keep hearing people talk about the repository - are they just talking about the PBI's on the webpage or is there a programme like snaptic where i can install stuff through a repo?

---

### Post by mips on 2007-04-14
You can install packages with pkg_add or you could compile from the ports collection.

---

### Post by darksong on 2007-04-14
thanks ;)

is there any way to get a graphical front to this or is it purley command line?

---

### Post by igknighted on 2007-04-14
> **darksong said:**
> thanks ;)

is there any way to get a graphical front to this or is it purley command line?

If you want a great graphical frontend, and don't mind compiling some from ports, try DesktopBSD... see a screenshot of the package manager in the thread next to this one.

---

### Post by darksong on 2007-04-14
thanks for the reply ;) i will be sure to check it out

---

### Post by Thulemanden on 2007-04-22
> **darksong said:**
> Can anyone tell me if there is another way to install software through it except PBI's? On the forums i keep hearing people talk about the repository - are they just talking about the PBI's on the webpage or is there a programme like snaptic where i can install stuff through a repo?

You can easily install DesktopBSD's package manager (port application) and install any of the 14,000 offers in a single click. Forget about compiling - only developers and bleeding edge junkies need compile (build) today. Besides it takes a war to do it in question of time.

---

### Post by JaceMan on 2007-05-19
Are you saying that you can EASILY install DesktopBSD's package manager on PC-BSD?  If so, I'm dusting off my old PC-BSD laptop today!

---

### Post by beartard on 2007-05-23
The DesktopBSD tools (package manager, network manager, etc.) can be installed on top of any FreeBSD derivative.

---

### Post by theonlyrealperson on 2007-06-07
> **Thulemanden said:**
> You can easily install DesktopBSD's package manager (port application) and install any of the 14,000 offers in a single click. Forget about compiling - only developers and bleeding edge junkies need compile (build) today. Besides it takes a war to do it in question of time.

LOL - I wish I knew that before I started my last FreeBSD installation.:D

Seriously, I love FreeBSD, and I was introduced to it through the 'easier to install and use' PC-BSD. I have nothing against PC-BSD, but I really enjoyed compiling my own kernel + xorg + kde and it's programs... Really I did! Sure it took a week to get a good fully-functional laptop going, but in the end I've got all the 'bleeding-edge' programs and it runs quick and errorless. And there is some great satisfaction in that.

Two things I have learned though, that may be of interest to other Newbies:

1. You are just asking for trouble if you have a fully up-to-date from the ports system and you use "pkg_add -r". I've had to forcefully rebuild ports from problems due to that many times. If you build your system from ports, stay with the ports. If you build your system from packages, stay with the packages (unless you upgrade your whole system). Packages are always (well, in my experience) behind the ports, and the dependencies won't play nice with each other.

2. If you install it onto a laptop with wifi - I've had a bunch of trouble with the Intel 2200BG driver for 6.2. It's hardly FreeBSD's fault, but there are some bugs that need to be worked out. (it's the iwi-firmware-kmod package). Strangely, the 6.1 Intel 2200BG driver iwi-firmware (which is what you get with PC-BSD) seemed a lot more stable.

---

### Post by Bachstelze on 2007-06-07
Absolutely no problem here on FBSD with an ipw 3945 WiFi adapter :)

---

### Post by theonlyrealperson on 2007-06-10
> **HymnToLife said:**
> Absolutely no problem here on FBSD with an ipw 3945 WiFi adapter :)

Huh, well, maybe I should deinstall it and then recompile it and see if it works better. 

Did they change the ipw driver between 6.1 and 6.2? They did for the 2200BG, and I will have to say I like the old one a lot better.

---

### Post by beartard on 2007-06-10
I had no trouble installing from ports on FreeBSD, but had an almost impossible time under DesktopBSD with that Intel kmod driver.  I ended up copying the modules from a FreeBSD install to DesktopBSD.  The thing would work, but only sporadically.  It was as if the thing would timeout and then reconnect when it was needed.  It worked, but it was annoying.

---

### Post by theonlyrealperson on 2007-06-10
> **beartard said:**
> I had no trouble installing from ports on FreeBSD, but had an almost impossible time under DesktopBSD with that Intel kmod driver.  I ended up copying the modules from a FreeBSD install to DesktopBSD.  The thing would work, but only sporadically.  It was as if the thing would timeout and then reconnect when it was needed.  It worked, but it was annoying.

That's really strange, because that's the same problem I have now with FreeBSD. Under DesktopBSD, I couldn't even get it to make. All I got was an "error code 1". PC-BSD, using FreeBSD 6.1 and the Intel Firmware driver, I had no problems at all.

---

### Post by beartard on 2007-06-10
I've never really used PC-BSD seriously.  I think when I installed it to try out, I still had a broadcom card in my laptop (which since met its demise via a 2lb hammer.) The thing that attracted me to DesktopBSD was that it was FreeBSD with some nice tools to make it work better on the desktop.  PC-BSD departs from the FreeBSD package/ports system in a way that made me uncomfortable, despite its great appearance.

But yeah, I did get the Intel modules compiled and semi-working under FreeBSD.  Then I copied them over to DesktopBSD and they semi-worked.  Try as I might, they never would compile under DesktopBSD.  Frankly, their forum users are not as helpful as the ones here.

My favorite reponse from a helpful user there, when another user asked a question about hardware support, was a terse "buy better hardware."  I love the OS, but if their user base can't quit being so snobbish about it, it won't ever leave the server.  Maybe that's a good thing?

---

### Post by theonlyrealperson on 2007-06-10
I agree with you on the difference of the forums, it's night and day. Even if you ask a stupid question here (as I have) you'll get a helpful answer as long as you ask nicely.

I read that same post over on the DBSD forums, with 'Oliver Herold'"s retort. I was not impressed. 

BSDForums is nice for searching, but it seem to be frequented very much.

I used PC-BSD for a couple of months and really liked it. The forums are decent too. I moved away because I liked the ports a lot, and wanted to "build my own" FreeBSD from the kernel up. With a minimal install and a few helpful directions from openaddict.com it was fun. I learned a lot as well.

I decided against DesktopBSD after I tried to get that intel wireless working, and saw that post. Too bad, the liveCD looked pretty cool.

---

