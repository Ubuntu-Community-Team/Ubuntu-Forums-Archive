---
title: "OpenBSD"
date: 2008-04-17
forum: BSD
---

### Post by Th3Professor on 2008-04-17
The intention of this thread is pretty light-hearted.

Some questions, really generic stuff...

1. Have you used OpenBSD?
2. Do you like OpenBSD? (Why?)
3. Do you dislike OpenBSD? (Why?)

:popcorn:

---

### Post by Sunnz on 2008-04-22
Yes I am an OpenBSD user here... I only have started using it since 4.0, isn't really that long ago.

It is more than just "secure by default" which I liked about OpenBSD... what I really like is its "Openness"... but you might wonder that Linux is open source as well!! Well it is the different approach to it... for example, it is very simple to look up the history of the kernel source, just go to the web site and browse it, it is there on the web, inside browser, a whole history of changes to it. Along with that you can pretty much just click through the whole system tree, and the ports, and poke around with it... 

Sure, you can browse the source for Ubuntu as well, but that's a whole different story, I still have no ideas where to find the exact source that was used to compile for the kernel that I see on a live running version of Ubuntu, well it is on lauchpad... somewhere!! The worst I have seen though, is that Ubuntu users sometimes don't even understand the whole process... I have seen on the forums where one asked how to get the source of the kernel used in Ubuntu, simply to be point to kernel.org... yea that's the vanilla kernel, not the kernel with Ubuntu tweaks in it. This is something you'll never see on an OpenBSD list.

I can probably just keep rambling for hours... so just to make it concise, I like the approach and OpenBSD devs focus on writing correct code; rather then just simply putting up code that runs and have no concerns of what it will become later. It is the engineering approach that they take that I can trust on; rather than the program by coincidence approach other people tend to make. It is also the logical decision they make that I tend to agree on, they actually reject binary blob drivers for a reason, because they are impossible to debug and the way drivers interacts with the kernel would cause severe problems, not that they are free software zealots like GNU with the gNewsense OS.

And of course, it all leads to the security thing... it is just really cool to know that Linux is already accepted to be hard to crack, just to realise that even the rare vulnerable apps you find on Linux, mostly does not do harm to OpenBSD at all!!

There are things that I dislike about OpenBSD... mostly common BSD problems though. 1, BSDs usually provide Linux emulation, but it is only available on i386, but not anything else, not even AMD64... it shouldn't be marginally more difficult than i386, since Linux is open source for the most part, and AMD64 Linux is pretty much on par i386 Linux these days. Perhaps it is due to the lack of developer interest... it is not a show stopper, however. 2, this is OpenBSD specific, the install CD just doesn't work with my CD-Rom, I have no ideas what's wrong with it, it can boot up the computer, and proceed to partition the hardware and everything... but paradoxically it cannot read from the CD, and so it cannot copy over the install files... everything I do an upgrade I had to put the file on a Flash drive before hand.

---

### Post by cammin on 2008-04-25
I agree with Sunnz. Haven't had his install problem, though.

My only problem with OpenBSD is the lack of readily available software. Not a big deal.

The only reason I'm not using it at the moment is because I'm using it's partition to try out NetBSD and FreeBSD 7.0

---

### Post by Th3Professor on 2008-05-01
I could answer my own questions I suppose...

I use OpenBSD.

There's nothing I dislike about it.

Just a few things I like about it and basically why:

1. It's very logical.
The entire system is set up in a way that is easy to figure out, even in that "non-GUI" kind of way. The whole infrastructure, on a big scale. On a small scale, the choice of applications and special OpenBSD ported apps.

2. Simplicity.
The K.I.S.S. motto plays out with OpenBSD. There is none of that silly unnecessary junk that comes with it. You have optimal control over how you'd like to build it. There are several "add-on" features that are not required (where several other systems do require them or do not give the choice to exclude them).

3. The obvious... "secure by default" and other well-known features.
It's solid. Stable. Secure. Functional. Portable. Standard. Correct. And it accels in cryptography.

There are more but that's enough for now.

The "Openness" reference that Sunnz made, I completely agree.

I'm also an advocate of the BSD licenses... more so than the GNU GPL.
They emphasize "copycenter" concepts, rather than copyright or copyleft, as in "take it down to the copy center and make as many copies as you want." OpenBSD took it another step, the ISC license, basically a 2-term BSD license, only without some unnecessary text.

Sunnz mentioned the simplicity in looking up the history of the kernel source - that's another great thing, specifically in OpenBSD, is their kernel is amazing, it is "correct".

Another bit I completely agree with in Sunnz message:
"...rather then just simply putting up code that runs and have no concerns of what it will become later." (Regarding correct code.)

A colleague of mine recently went to a conference where they practiced penetration. They used various Windows OSs and Linux set-ups, though they never used OpenBSD. The reason was basically that it's just too hard to penetrate, if it at all.

I don't mind that OpenBSD doesn't have some applications in their ports tree. What they do have is more than enough to run a great system, and although you can still compile from source or make necessary adjustments to work non-native apps into the system, there's still plenty to go around just within their ports.

I've had good luck with the Linux emulation, though haven't used it for more than a couple simple programs. I definitely would say install the emulator (and any Linux-based apps) from binaries and not from source. I attempted compiling that from source once and 3 days of compiling, and eating up about 90% of the harddrive, passed before I scrapped it and went for the binaries.

Sunnz:
Have you had any luck with that install CD or a new one?

---

### Post by lespaul_rentals on 2008-05-05
I tried OpenBSD for a while.  I think it is a great operating system and made for a great learning experience.  I also really like Theo de Raadt.  However, I don't like they way there's no automated upgrades for software.  I can definitely see the advantages to that, but considering I am just experimenting with a home server setup and I'm busy, I don't have time to manually patch all the software.

---

### Post by radtek on 2008-09-08
What's to dislike? I installed it three times this afternoon just to see how it installed. Installed the same all three times. Not used to KDE, but I've used it before. Top shows BSD is running 60 processes compared to 8.04's 150! Also 8.04 uses 2x more ram to run those extra programs. I love how snappy it is.

A few installation woes such as wifi(usb) but really I expected that. Boot time is lengthy however- somewhat longer than Ubuntu has been. I was surprised but this may be hardware based too.

Perfect? Nothing ever is...

---

### Post by Th3Professor on 2008-09-08
Plus... OpenBSD is one of the most solid systems currently available. :)

---

### Post by mips on 2008-09-08
1. Have you used OpenBSD?

Yes.

2. Do you like OpenBSD? (Why?)

Yes. Simple, secure, easy. Appreciate their goals.

3. Do you dislike OpenBSD? (Why?)

No.

---

### Post by LateNiteTV on 2008-09-09
"secure by default" doesnt mean much, really. that can only be applied to the default install. which is the base system. once you start adding packages that all flies out the window.

---

### Post by mohitchawla on 2008-09-17
I like OpenBSD's installation procedure. I like OpenBSD's installation documentation, actually.

That's pretty much it.

I couldn't get internet working with it, that is no downloads or display of web pages in Lynx, although ping requests to websites were successfully responded back. A problem I thought I could address to someone on some BSD forums, only to be disgusted with the sight of sex, viagra and pr0n SPAM. That was a *big* disappointment.

I'd surely want to give it a try, but with not much community support ( that's free of spam), guess I'd rather stick to Linux.

Anyway, gonna try PC BSD's latest release and see if it works fine.

---

### Post by mips on 2008-09-18
> **mohitchawla said:**
>  A problem I thought I could address to someone on some BSD forums, only to be disgusted with the sight of sex, viagra and pr0n SPAM. That was a *big* disappointment.

I'd surely want to give it a try, but with not much community support ( that's free of spam), guess I'd rather stick to Linux.
.

For some odd reason the staff there just ignored the spam. Most users have migrated to another forum without spam. Unfortunately I cannot remember the sites name. Maybe google 'BSD Forum'.

---

### Post by Canis familiaris on 2008-09-18
What advantages does OpenBSD have over FreeBSD? Is there any incentive for a desktop FreeBSD/PC-BSD user to use OpenBSD?

---

### Post by -Rick- on 2008-09-19
> **mips said:**
> For some odd reason the staff there just ignored the spam. Most users have migrated to another forum without spam. Unfortunately I cannot remember the sites name. Maybe google 'BSD Forum'.
[Link]("http://daemonforums.org/")

---

### Post by Th3Professor on 2008-09-19
> **Anurag_panda said:**
> What advantages does OpenBSD have over FreeBSD? Is there any incentive for a desktop FreeBSD/PC-BSD user to use OpenBSD?

<sarcasm> "Goody, someone chimed in on FreeBSD in an OpenBSD thread... that's never happened before!" </sarcasm>

<wink wink> (just teasin' around) ;)

---

### Post by LateNiteTV on 2008-09-23
> **mohitchawla said:**
> I like OpenBSD's installation procedure. I like OpenBSD's installation documentation, actually.

That's pretty much it.

I couldn't get internet working with it, that is no downloads or display of web pages in Lynx, although ping requests to websites were successfully responded back. A problem I thought I could address to someone on some BSD forums, only to be disgusted with the sight of sex, viagra and pr0n SPAM. That was a *big* disappointment.

I'd surely want to give it a try, but with not much community support ( that's free of spam), guess I'd rather stick to Linux.

Anyway, gonna try PC BSD's latest release and see if it works fine.

daemonforums.org
bsdforums new place.

---

### Post by cardinals_fan on 2008-09-23
[BSDnexus]("http://forums.bsdnexus.com/") has some decent (if sparse) forums.

---

### Post by LateNiteTV on 2008-09-26
> **Anurag_panda said:**
> What advantages does OpenBSD have over FreeBSD? Is there any incentive for a desktop FreeBSD/PC-BSD user to use OpenBSD?

i would say none.

---

### Post by mips on 2008-09-27
> **LateNiteTV said:**
> i would say none.

I would say it is more secure out of the box. They also do not allow binary blobs as you don't know what's in them.

---

### Post by Niniel on 2008-09-29
I see this argument a lot... Speaking as a lousy amateur, I have to wonder though if it is anything more than just hot air though... Who knows enough about programming, and has the time to examine all the code, to make sure that there's nothing hidden somewhere?
Maybe the type of people who'd run OpenBSD do...

---

### Post by Bachstelze on 2008-09-30
> **Niniel said:**
> Who knows enough about programming, and has the time to examine all the code, to make sure that there's nothing hidden somewhere?
Maybe the type of people who'd run OpenBSD do...

The people who make it do, too. You can think whatever you want about Theo, but you can't deny he's an extremely skilled hacker. You can trust him, he knows his stuff.

---

### Post by regomodo on 2008-11-01
I've just briefly stepped into OpenBSD and really like its aims and installer.

What i'm not too sure about is it package management tool. Coming from pacman/emerge/apt background it is a bit underwhelming. At least it is not as bad as Slackware's pkg management.

---

### Post by cammin on 2008-11-01
This thread just coincidentally gets bumped on the day OpenBSD 4.4 gets released. Sneaky :)

---

### Post by Th3Professor on 2008-11-02
> **regomodo said:**
> I've just briefly stepped into OpenBSD and really like its aims and installer.

What i'm not too sure about is it package management tool. Coming from pacman/emerge/apt background it is a bit underwhelming. At least it is not as bad as Slackware's pkg management.

Just don't compile from source in OBSD unless you have to. Otherwise, the package management is easy cheesy. Ditto for slackware. If you use their package management it's easy cheesy. ;)

> **cammin said:**
> This thread just coincidentally gets bumped on the day OpenBSD 4.4 gets released. Sneaky :)

Woohoo! :guitar:

One of my favorite things about OpenBSD is the release of a new geeky-but-very-cool song with each release. :)

---

### Post by PegMonster on 2008-11-02
I haven't tried it yet but am keen to.

How is the hardware support in OpenBSD as opposed to FreeBSD?

I really like FreeBSD, but my hardware doesn't.
(I can't even boot FreeBSD from my Compaq notebook)

J

---

### Post by tuxxy on 2008-11-02
For a desktop I would go freeBSD if had to, server maybe OpenBSD but then again freeBSD also good for server tasks but if your really into security then Open although I prefer linux for a desktop :)

---

### Post by Th3Professor on 2008-11-02
OpenBSD

---

### Post by PegMonster on 2008-11-02
> **Th3Professor said:**
> OpenBSD

Is this in regards to my question about hardware?
If so can you elaborate a little please?

If not, just disregard this post.

J

---

### Post by cammin on 2008-11-03
I'd try OpenBSD, even if FreeBSD doesn't work.
Things are different enough that whatever is causing your problem in FreeBSD might not be an issue in OpenBSD.

As far as FreeBSD specifically, try booting with acpi support disabled. (it's one of the options in the boot menu)
While I haven't had a problem with ACPI in FreeBSD specifically, I've had problems booting with it enabled in NetBSD and DragonFlyBSD.

---

### Post by PegMonster on 2008-11-03
> **cammin said:**
> As far as FreeBSD specifically, try booting with acpi support disabled. (it's one of the options in the boot menu) While I haven't had a problem with ACPI in FreeBSD specifically, I've had problems booting with it enabled in NetBSD and DragonFlyBSD.

I have tried that and more. I found out that with my notebook series I have to set hints prior to booting for apic (not acpi, but apic). Problem is, most of the time it doesn't even load to the beastie menu. And when it does, it very rarely manages to boot anyway, just gives me errors. It's really weird. Happens with PCBSD also. And I have made sure the iso's are burned correctly and chcksum'd ok etc. Still no go. And my bios gives me next to no configuration options which doesn't help.

Anyway, I will give OpenBSD a try.

Cheers

J

---

### Post by LateNiteTV on 2008-11-04
> **Th3Professor said:**
> **Just don't compile from source in OBSD unless you have to. Otherwise, the package management is easy cheesy. Ditto for slackware. If you use their package management it's easy cheesy. ;)**


i ALWAYS compile everything from source. 
```
cd /usr/ports/x11-wm/windowmaker; make install clean
```

you get the optimizations from make.conf as opposed to just installing a 386 binary.

---

### Post by regomodo on 2008-11-04
I've given up on openBSD. It's not fast as they claim. The system locks up on heavyish hdd access in a similar manner when i'm not using completely-fair-queuing in Linux. It uses more RAM, BAD acpi/apm support (it wont turn off my laptop), not suited for Desktop/Laptop use, and has a lot of old packages.

I think i'll stick with (hardened) Gentoo thanks.

---

### Post by Th3Professor on 2008-11-05
> **LateNiteTV said:**
> i ALWAYS compile everything from source. 
```
cd /usr/ports/x11-wm/windowmaker; make install clean
```you get the optimizations from make.conf as opposed to just installing a 386 binary.

I used to always compile/install from source until I ran into the Open Office snafu, which needs to be installed via binary. There is no point in using source unless you want to tweak it, which I still do time to time, though if you just want a generic install - which in many cases works just as well, if not better - then using OpenBSD's own package management is ideal.

> **regomodo said:**
> I've given up on openBSD. It's not fast as they claim. The system locks up on heavyish hdd access in a similar manner when i'm not using completely-fair-queuing in Linux. It uses more RAM, BAD acpi/apm support (it wont turn off my laptop), not suited for Desktop/Laptop use, and has a lot of old packages.

I think i'll stick with (hardened) Gentoo thanks.

What exactly do you mean by not fast and heavyish hdd?

OpenBSD is the optimal system for specific purposes, obviously not the purposes you have in mind. ;)

---

### Post by regomodo on 2008-11-06
> **Th3Professor said:**
> 
What exactly do you mean by not fast and heavyish hdd?


By not fast i mean everything seems to take longer such as load times, navigating through applications. "Heavyish hdd" refers to hdd access. It seems everytime i load a reasonable size application (firefox,abiword,thunderbird) the system starts to become unresponsive to user inputs such as keyboards and mice. Once the app is loaded it stops.

---

### Post by LateNiteTV on 2008-11-06
try configuring a custom kernel.

---

### Post by Th3Professor on 2008-11-18
> **LateNiteTV said:**
> try configuring a custom kernel.

regomodo's running 3+ gentoo set-ups, perhaps custom kernel is actually a viable option for them. ;) ...that is... what one would assume of a gentoo user... though the irony behind bsd kernel is you really don't have to customize it, it's great the way it is. :)

---

### Post by Sunnz on 2008-11-23
> **Th3Professor said:**
> 
Sunnz:
Have you had any luck with that install CD or a new one?

None of the CD works, not even 4.4 brought from the OpenBSD store.

However I managed to swap my DVD Drive with a friend, mine was a IDE one and now I got a SATA one, worked flawlessly, I have no ideas why the cable makes such a difference for OpenBSD... but now it works, and I am very happy with it!!

P.S. OpenBSD has surely come a long way, 4 pages on here already since last time I come to this forum!! Whoohoo!!!

:popcorn:

---

### Post by scottro on 2008-11-23
Just re the forums being full of spam comment.  (bsdforums, with a comment that is a few months old)

As the administrator of the site apparently became too busy to watch it, it was overrun by spammers.

There is now, aside from the excellent bsdnexus forums mentioned above, daemonforums.org.   (I see that people have linked to it, but haven't given that much of an explanation.)

Most of the openbsd gurus from the old forum are there now.  
(There's also a new forums.freebsd.org which is, oddly enough, FreeBSD specific.)

---

### Post by the8thstar on 2008-11-23
I tried FreeBSD but never went further than a simple xterm environment. For some reason Gnome never showed up. 

I didn't try OpenBSD for the simple reason that it comes with KDE and not Gnome by default. That was the ultimate turn-off.

---

### Post by mips on 2008-11-23
> **the8thstar said:**
> 
I didn't try OpenBSD for the simple reason that it comes with KDE and not Gnome by default. That was the ultimate turn-off.

I think you are mistaken, OpenBSD does NOT come with any DE installed by default. You choose what you want to install & then install from the ports collection.

---

### Post by vermaden on 2008-11-23
You have to configure everything, like in Arch linux for example.

---

### Post by LateNiteTV on 2008-11-24
> **the8thstar said:**
> I tried FreeBSD but never went further than a simple xterm environment. For some reason Gnome never showed up. 

I didn't try OpenBSD for the simple reason that it comes with KDE and not Gnome by default. That was the ultimate turn-off.

i havent installed openbsd in quite some time, but im guessing that theres not an option to install gnome during the system installation...?

pkg_add -r gnomewhateverwhatever

edit your .xinitrc file to start gnome when you enter startx and ur good to go.

---

### Post by chachawpi on 2008-11-24
I don't have any desktop experience with OpenBSD, but as a web server it is great.  With Apache being chrooted by default, there is a lot of tedious setup time saved.  I just wish my company had more servers I could port over to OpenBSD.

---

### Post by mips on 2008-11-25
> **LateNiteTV said:**
> i havent installed openbsd in quite some time, but im guessing that theres not an option to install gnome during the system installation...?


Not that I'm aware of. I'm pretty sure that you can customise the installer or create a install script if you would like to.

Why not just install it afterwards?

---

### Post by Th3Professor on 2008-11-25
If someone wants gnome on obsd then they add it just like they'd add anything else. The OS is posix compliant just like several others. One of the greatest features in OpenBSD is that you build it how you want it. :)

---

### Post by the8thstar on 2008-11-25
My mistake, I confused OpenBSD with PC-BSD. 

Anyhow, no GUI by default = "Homey don't play that!" as far as I'm concerned. It's just MY opinion.

---

### Post by LateNiteTV on 2008-11-25
lol dude all you have to do is install the damn thing. "homie dont be lazy and type a couple commands"

---

### Post by Sunnz on 2008-11-25
I like the OpenBSD installer as is, it is to the point, it is more than adequate as far as installers goes - for a good rock solid OS it is not like it needs to be reinstalled every month, it just doesn't need to be all fancy and stuff, it just needs to be robust and work. And I hope this doesn't sound rude, but if Homey don't play it just because he don't want to install some software, (who doesn't install additional software on any OS?) then perhaps OpenBSD isn't the right OS for them.

---

### Post by Th3Professor on 2008-11-26
> **LateNiteTV said:**
> lol dude all you have to do is install the damn thing. "homie dont be lazy and type a couple commands"

Freakin' hilarious!

:lolflag:

> **Sunnz said:**
> I like the OpenBSD installer as is, it is to the point, it is more than adequate as far as installers goes - for a good rock solid OS it is not like it needs to be reinstalled every month, it just doesn't need to be all fancy and stuff, it just needs to be robust and work. And I hope this doesn't sound rude, but if Homey don't play it just because he don't want to install some software, (who doesn't install additional software on any OS?) then perhaps OpenBSD isn't the right OS for them.

:D

---

### Post by the8thstar on 2008-11-27
> **LateNiteTV said:**
> lol dude all you have to do is install the damn thing. "homie dont be lazy and type a couple commands"

"I don't think so" :)

Well, I DID try. Problem was, the thing never worked and I just wiped it off the partition and installed Solaris 10 instead (which is a true UNIX with a working GUI at boot).

---

### Post by cammin on 2008-11-27
Not that you'll bother with it again, but you probably forgot to set the environment variable for the package mirror.

export PKG_PATH=ftp://ftp.openbsd.org/pub/OpenBSD/4.4/packages/i386/

---

### Post by Th3Professor on 2008-11-27
[FONT=Times New Roman]> **the8thstar said:**
> "I don't think so"

 Well, of course nobody has to "type a couple commands" if they don't want to. lol You said better than anybody else with, "It's just MY opinion." The moment someone chooses to disregard another persons opinion and tries to force-feed them their own opinion on a subject is the moment they begin blowing gas out their a$$. ;)

 Those advocating CLI have a valid point.
 Those advocating GUI have a valid point.

It sounds like you're simply saying that you like GUI and don't like CLI. That's totally cool... I don't hear anybody bible-beatin' ya otherwise. <grin>

 > **the8thstar said:**
> Well, I DID try.

 Are you referring to PC-BSD or another *BSD?

 What did you try?

> **the8thstar said:**
> Problem was, the thing never worked and I just wiped it off the partition and installed Solaris 10 instead

 Awesome! In my opinion, Solaris is an excellent OS. Sun has revolutionized computing on many occasions.

 > **the8thstar said:**
> (which is a true UNIX with a working GUI at boot).

:neutral: Just a heads up: you might want to be careful with a statement like that.

 If you want to get into semantics - and *not* start a "flame war" - then **UNIX** (not Unix or unix) is a product of AT&T... not Sun. Yes, there have been relations between the two, even among many other *nix systems, though a "true" "UNIX" in the all-caps sense is nothing of the sort.

If you are referring to SysV, then Solaris... which is from Sun... which is currently known as a SysV system... did not originate from SysV alone but, rather, 4.1BSD and V7. Yes. BSD was there in the beginning of Sun.

It is true that BSD came from UNIX, which included the different Editions (including V5), though code from both "BSD" and "SysV" type systems were included in the original Sun operating system. (Using "SysV" generically as the "mostly non-BSD Unix".)

 Here's a very condensed and extremely truncated look at *nix timeline, and I'll only 
include the systems that have been mentioned recently in this (our OpenBSD) thread, and I'll include Linux basics since this is a linux forum:

**1969, UNIX (as UNICS), at AT&T/Bell Labs.**
**1971, UNIX V1, "UNIX Time-Sharing System First Edition (V1)".**
 1975, V6.
**1978, 1BSD (with a V6 influence).**
 1981, UNIX System III (late-1981).[B]
1982, SunOS (from 4.1BSD and UniSoft UniPlus (V7)).[/B]
**1983, UNIX System V ("SysV").**
 1984, Minix (late-1984, with a 4.1BSD and V7 influence, eventually spawned Linux).
 1984, GNU.
 1985, FSF.
 1986, 4.3BSD.
 1987, Minix (version 1.0).
 1988, OSF.
**1990, SunOS 4.1.1 is given an additional title, Solaris 1 (which includes 4.3BSD).**
 1991, BSD Net/2 (4.3BSD influence, later NetBSD, FreeBSD, and OpenBSD).
**1991, Linux (0.01) (mid-1991, with a Minix influence).**
 1992, Solaris 2 (both x86 and sparc architectures), a second line of Solaris.
 1993, AT&T sales UNIX to Novell (January 1993).
 1993, NetBSD (early 1993, which eventually spawned OpenBSD).
 1993, Slackware Linux (released in July, spawns SuSE (Novell now owns) and more).
 1993, Debian Linux (released in August, spawns Ubuntu and more).
**1993, FreeBSD (late 1993, which eventually spawned PC-BSD).**
 1994, Red Hat Linux.
 1994, Novell gives "UNIX" trademark to The Open Group (aka "X/Open Company").
 1994, Novell sales UNIX source code to SCO.
**1995, OpenBSD (with a NetBSD influence).**
 1999, Enoch Linux (renamed to Gentoo Linux in 2002).
 2002, Arch Linux.
**2004, Ubuntu Linux (released in October, Debian influence).**
**2005, Solaris 10 ("official" release, from SunOS).**
 2005, OpenSolaris (about 6 months after Solaris 10).
**2005, PC-BSD (mid-2005, with a FreeBSD influence).**
[I]2008, FreeBSD 7.0 (early-2008 ).
2008, PC-BSD 7 (mid-to-late-2008 ).
2008, Ubuntu 8.10 (10/08 ).
2008, Solaris 10 10/08.
2008, OpenBSD 4.4 (10/08 ).[/I]

In 1987, AT&T's system (the real UNIX) and Sun's system (a Unix spawn) united. This spawned the OSF, another evolution of open source, which was a response to the proprietary contracts between AT&T and Sun. In other words, BSD started branching out and expanding as a response to the AT&T/Sun deal.

In 1993, AT&T sold UNIX to Novell. More branching out and expanding of all *nix systems took place at this point, notably of the open source variety. The three early big dogs of BSD (NetBSD, FreeBSD, OpenBSD) and the three early big dogs of Linux (Slackware, Debian, and Red Hat) were developed, from which the plethora of other systems were spawned.

 In 1994, Novell gave the UNIX name to the Open Group and sold the UNIX source code to SCO. The rest is history.

This was also the early stage of general SysV+BSD merging, which has since developed into an extremely interchangeable aspect of *all* *nix systems.

The real UNIX, by name and by code, is presently only one system - not multiple systems - although the multiple Unix (not UNIX) systems and Unix-based (not Unix) systems, aka GNU/Linux, that we have today inevitably share some of that UNIX code. The real UNIX includes the likes of UNIX 93, UNIX 95, UNIX 98, UNIX 03. What we have and classify as POSIX compliant, among all *nix systems, is based off of UNIX. There is also more of an open source involvement with UNIX now than there used to be.

When you get into the GUI of all of these systems, you immediately introduce the open community of software development to the "operating system", which includes anything on top of the kernel.

Even Solaris, in the more recent revisions of version 10, has an extremely Linux-friendly foundation, including the GUI. Likewise, the *BSD operating systems have also had the extremely Linux-friendly foundation, including the GUI.

 All in all, in response to your:
 "...which is a true UNIX with a working GUI at boot..."

 I have to say...

 Regarding the "UNIX" specification:
 All Unix and Linux set-ups are "true" Unix-like systems. However, **none** of them - not even Solaris - are true UNIX systems.

In other words: There can be only one. (...and Solaris ain't it.)

 Regarding a working GUI at boot:
 The vast majority of Unix and Linux installs include GUI as defaults to boot to. This includes OpenBSD - when you go through the install process you are given the option of installing X, which *is* a GUI.

 Also note the different types of GUIs, especially DEs and WMs.

 A destktop environment (DE) is something like GNOME and KDE.
 A window manager (WM) is something like Fluxbox and FVWM.

 Note the differences:
 DE = a WM with extra applications bundled/packaged together.
 WM = the GUI environment without the extra packages.

When you install OpenBSD, for example, you are given an initial X (GUI) environment, a WM specifically. If you want a DE like GNOME, you can do something like this:

 1. Find your OpenBSD mirror at [http://www.openbsd.org]("http://www.openbsd.org/") (for installing apps).

 2. Set up your package path so you can add packages:

```
$ export pkg_path=ftp://<your.ftp.mirror>/pub/OpenBSD/4.4/packages/`machine -a`/
``` (Or replace 4.4 with a newer version when OpenBSD releases future versions.)

 You can also add the path to your root's profile, open this in a text editor:

 ```
/root/.profile
``` ...and add these 2 lines:

 ```
export pkg_path=ftp://your.ftp.mirror/pub/OpenBSD/4.4/packages/`machine -a`/
export fetch_packages=yes
``` (We work with the "root" account's profile since we use either "sudo" or "su", aka root, to install/remove/etc. packages. If you are an Ubuntu user who is scared of using a root account, then you might opt to do a little research on the benefits of using root. I advocate using root, though that's just me... though, I do not advocate use of root by someone or anyone who is likely to screw up the computer. lol)

 Remember:
 > With great power comes great responsibility. 3. Add your packages:

 You'll probably want both GNOME and the GNOME log-in manager, which are "gnome-session" and "gdm", respectively.

```
$ sudo pkg_add gnome-session-2.20.3p11.tgz
``` ```
$ sudo pkg_add gdm-2.20.2p6.tgz
``` You can add flags/options to the pkg_add command if you like, such as "-i" for interactive, "-v" for verbose, or more.

 4. Set up your new GUI to load at boot:

```
echo "/usr/local/bin/gdm -nodaemon &" >> /etc/rc.local
``` 5. Add "/usr/local/bin" to your PATH environment, within "/root/.profile" if it's not already:

```
PATH=$HOME/bin:/bin:/sbin:/usr/bin:/usr/X11R6/bin:/usr/local/bin:/usr/local/sbin
``` (This will let your binaries in your user's local path load.)

 (Make sure there is not a "." or ":." at the end of the PATH line (for security purposes.))

 Note that you can install either of 2 basic ways:

  A) ports (/usr/ports, not recommended)
   You can refer to this link for more: [http://www.openbsd.org/ports.html](http://www.openbsd.org/ports.html)

   or

   B) packages (pkg_path and pkg_add, the recommended way)
   You can refer to this link for more: [http://www.openbsd.org/faq/faq15.html#Easy](http://www.openbsd.org/faq/faq15.html#Easy)

Ports = compile from source, which is okay, and offers more flexibility, though could be time-consuming and take up more space during the install process.

 Packages = the "pkg_" type commands are part of OpenBSD's package management system, which still offers flexibility, though it installs apps faster and without consuming more space during the install process.

Some additional "pkg_" commands...

View what you have installed:
```
pkg_info
```Updates:
  ```
pkg_add -u <applications>
```Deinstall applications:
  ```
pkg_delete <applications>
```That is almost as easy as typing "ls -la" or anything of that sort. :)

Using the command line isn't as bad as it might seem at first. Once you get the hang of things - the simple commands - you can more comfortably take on the more complex commands. 

Just for the heck of it, I'll include more goodies:

A. Install ports tree:

1. Download the following files from the ..."/pub/OpenBSD/"...(etc.) directory:

 ```
src.tar.gz
``` ```
ports.tar.gz
``` 2. Unzip/untar the src file into:

```
/usr/src/
``` ...and unzip/untar the ports file into:

```
/usr/ports/
``` In other words, do this:

```
cd /usr/src/
tar xvfz /mnt/cdrom/src.tar.gz
cd /usr/
tar xvfz /mnt/cdrom/ports.tar.gz
```B. Set up Java:

1. Retrieve Sun JDK (newest version) via:
[http://download.java.net/tiger/tiger_u12/](http://download.java.net/tiger/tiger_u12/)

You'll want the files with this info in their names:
 jdk-*src*jar
 jdk-*bin*jar

2. Retrieve bsd-jdk*patches*.tar.bz2 via:
[http://www.eyesbeyond.com/freebsddom/java/jdk15.html](http://www.eyesbeyond.com/freebsddom/java/jdk15.html)

(...links might refer to JDK 1.5, you may need a newer version.)

3. Retrieve jdk-*solaris*<arch>*.tar.Z via:
[http://java.sun.com/products/archive/j2se/5.0_12/index.html](http://java.sun.com/products/archive/j2se/5.0_12/index.html)

4. Retriev xalan-j*-bin.tar.gz via:
[http://www.apache.org/dist/xml/xalan-j/](http://www.apache.org/dist/xml/xalan-j/)

If you're curious why Java is a more involved install process, feel free to ask Theo de Raadt. lol. <wink>

 5. Check for possible manual fetching of files:

Go to "/usr/ports/devel/jdk/<version>" and type "make" (no quotes).

It may ask for your guidance if necessary, though will provide address and file that it needs. Download the files to this directory: "/usr/ports/distfiles/". Continue the build.

6. Follow any steps that you are prompted with after installation if you'd like to apply Java plugins to extra apps like browsers.

7. Add Java executable to your shell config file:

If you're using Korn shell, go into "~/.profile" (if you're using BASH, go into "~/.bashrc"). Find the PATH environment in the profile and add this to it: "/usr/local/jdk-<yourversion>/bin" (make sure there is no "." at the end).

8. Some apps require "java_home", add this line to that file: "export JAVA_HOME=/usr/local/jdk-<yourversion>/" (and log out and back in).

C. Enable Linux (binary support):

This part - along everything else, except Java - can be fairly simple if you follow the correct steps/process.

1. Edit this config file:

```
/etc/sysctl.conf
``` *Uncomment* the lines of your choice, such as Linux support:

```
kern.emul.linux=1
``` 2. Install "fedora_base" via pkg_add.

3. Create "/proc".

4. Update "fstab" (/etc/fstab) file, adding this line: "/proc  /proc  procfs  rw,linux  0 0"

D. SMP support for dual-core, quad-core, etc.:

1. If you are using a computer with a multi-core CPU, install "bsd.mp" (copy it to your root ("/") directory).

 2. Test bsd.mp at boot prompt, prior to init. Type "bsd.mp" (no quotes) and press enter.

 3. Make the change permanent by going to the / (root) directory and typing:

```
mv bsd.mp bsd
``` I could go on and on... but this is already lengthy enough of a post. 

  I hope it helps. :D[/FONT]

---

### Post by Sunnz on 2008-11-28
lol @Th3Professor, is that the OpenBSD faq in a nutshell? :D

I think what he meant by "real UNIX" is that Sun Microsystems can use the **Trademark** "UNIX" as they please, that is, till April 2009 anyway:

[http://www.opengroup.org/openbrand/certificates/1180p.pdf](http://www.opengroup.org/openbrand/certificates/1180p.pdf)

It just happens that The Open Group owns the *trademark* of "UNIX", all in capital letters. Anybody wants to use that trademark have to get The Open Group's permission for it.

The Open Group does do the correct thing and do require some certification in order to allow people to use that trademark. But at the end of the day, it is just a trademark, The Open Group could have give it out freely any way they want...

And oh look, Mac OS X has the same trademark license agreement too:

[http://www.opengroup.org/openbrand/certificates/1190p.pdf](http://www.opengroup.org/openbrand/certificates/1190p.pdf)

Are Macs Unix? Technically, yea... but does it feel like one when using it? Far from it, especially when you into the iStuff.

OpenBSD and BSDs in general, do feel more like a real Unix system in every way, the clean interface, have every program does one thing and do it well, that programs work together to make complex things done, simple in the implementation... those are the very basis of the *Unix philosophy*; the only differences is that they don't pay a huge sum of money to the Open Group to use the "UNIX" trademark, it is just not important.

---

### Post by Th3Professor on 2008-11-28
> **Sunnz said:**
> lol @Th3Professor, is that the OpenBSD faq in a nutshell? :D

I think what he meant by "real UNIX" is that Sun Microsystems can use the **Trademark** "UNIX" as they please, that is, till April 2009 anyway:

[http://www.opengroup.org/openbrand/certificates/1180p.pdf](http://www.opengroup.org/openbrand/certificates/1180p.pdf)

It just happens that The Open Group owns the *trademark* of "UNIX", all in capital letters. Anybody wants to use that trademark have to get The Open Group's permission for it.

The Open Group does do the correct thing and do require some certification in order to allow people to use that trademark. But at the end of the day, it is just a trademark, The Open Group could have give it out freely any way they want...

And oh look, Mac OS X has the same trademark license agreement too:

[http://www.opengroup.org/openbrand/certificates/1190p.pdf](http://www.opengroup.org/openbrand/certificates/1190p.pdf)

Are Macs Unix? Technically, yea... but does it feel like one when using it? Far from it, especially when you into the iStuff.

OpenBSD and BSDs in general, do feel more like a real Unix system in every way, the clean interface, have every program does one thing and do it well, that programs work together to make complex things done, simple in the implementation... those are the very basis of the *Unix philosophy*; the only differences is that they don't pay a huge sum of money to the Open Group to use the "UNIX" trademark, it is just not important.

Keyword: Clean.

:D

---

### Post by the8thstar on 2008-11-28
No flamewar intended. I used the label Unix to define a whole family of  OS; in this I put all *BSD, OS X and Solaris. Linux is a Unix-like.

---

