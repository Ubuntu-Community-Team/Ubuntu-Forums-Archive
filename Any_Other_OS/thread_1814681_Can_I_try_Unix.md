---
title: "Can I try Unix"
date: 2011-07-29
forum: Any Other OS
---

### Post by tech291083 on 2011-07-29
Hi,

I am thinking of trying Unix - 32 bit OS, but which version I should go for? Where do I get it downloaded from?  Does it contain any GUIs for new users like myself? Please share your experience with Unix. Thanks

---

### Post by boydrice on 2011-07-29
> **tech291083 said:**
> Hi,

I am thinking of trying Unix - 32 bit OS, but which version I should go for? Where do I get it downloaded from?  Does it contain any GUIs for new users like myself? Please share your experience with Unix. Thanks

There is no one true official Unix.  There are operating systems that are certified as Unix like Solaris, OS X, HP-UX, and IBM AIX.  The majority of OS certified as Unix are designed as a server OS with OS X being the exception to the rule.  If you want a true Unix-like experience then I suggest you try FreeBSD, NetBSD, or OpenBSD.  These Unix-like OS are server orientated but can be made into a fine desktop. If you want it done all for you then look at PC-BSD which the Ubuntu of FreeBSD.  Of course if you go that route you won't see much different than that of a Linux (another Unix-like OS but less similar to Unix than BSD) distro other than less hardware compatibility.

---

### Post by tech291083 on 2011-07-29
> **boydrice said:**
> Solaris, OS X, HP-UX, and IBM AIX....I suggest you try FreeBSD, NetBSD, or OpenBSD. Look at PC-BSD which the Ubuntu of FreeBSD. 


Yes, I have heard of them all, and that is why I would love to know from you as to which one is the closest one to Unix philosophy. But you have mentioned PC-BSD, which is the Ubuntu of FreeBSD, then I am going to try this one first. Tell me more about it. I will try to see where I can download it from. Thanks

---

### Post by tech291083 on 2011-07-29
Yes, here is what I found in line with your opinion of PC BSD.

[http://en.wikipedia.org/wiki/FreeBSD#Linux_compatibility](http://en.wikipedia.org/wiki/FreeBSD#Linux_compatibility)

> There are a number of software distributions based on FreeBSD including:
 
[LIST]
[*][PC-BSD]("http://en.wikipedia.org/wiki/PC-BSD") (aimed at home users and workstations)
[*][DesktopBSD]("http://en.wikipedia.org/wiki/DesktopBSD") (aimed at home users and workstations)
[*][FreeSBIE]("http://en.wikipedia.org/wiki/FreeSBIE") ([live CD]("http://en.wikipedia.org/wiki/Live_CD"))
[*]Frenzy ([live CD]("http://en.wikipedia.org/wiki/Live_CD"))
[*][GhostBSD]("http://en.wikipedia.org/wiki/GhostBSD") (Gnome-based live CD)
[*][m0n0wall]("http://en.wikipedia.org/wiki/M0n0wall") (firewall)
[*][pfSense]("http://en.wikipedia.org/wiki/PfSense") (firewall)
[*][FreeNAS]("http://en.wikipedia.org/wiki/FreeNAS") (for network attached storage)
[*]AuthServ (for network servers & storage)
[/LIST]
 All these distributions have no or only minor changes when compared with the original FreeBSD base system. The main difference to the original FreeBSD is that they come with pre-installed and pre-configured software for specific use cases.

---

### Post by boydrice on 2011-07-29
Honestly I would say try plain FreeBSD or OpenBSD over PC-BSD to get a real Unix-like experience.  GUIs are just about the same in every distro/BSD.  KDE is still KDE, GNOME is still GNOME, etc.  It is the under the hood stuff where the real differences lie.  The documentation for the BSDs is just outstanding and if you follow it you should not have too many issues.

If you do go with PC-BSD beware that it uses GPT by default, not that there is anything wrong with it but it will bomb-out traditional installers like cfdisk.  Also if you hate KDE (default in PC-BSD although that will change in PC-BSD 9) there is GhostBSD which has similar goals as PC-BSD but uses GNOME as the default.

---

### Post by tech291083 on 2011-07-29
> **boydrice said:**
> Honestly I would say try plain FreeBSD or OpenBSD over PC-BSD to get a real Unix-like experience. 

If you do go with PC-BSD beware that it uses GPT by default, not that there is anything wrong with it but it will bomb-out traditional installers like cfdisk.  Also if you hate KDE (default in PC-BSD although that will change in PC-BSD 9) there is GhostBSD which has similar goals as PC-BSD but uses GNOME as the default.

Ok, I am a bit confused here and need your help. Which is the one I should go for? If you say plain then where do I download it from? Please guide me. Thanks

---

### Post by tech291083 on 2011-07-29
Ok, here is the plain FreeBSD download page. I am going for DVD iso so I think I should go for the 2017993 KB file, right?

[FreeBSD-8.2-RELEASE-i386-dvd1.iso.xz]("ftp://ftp.freebsd.org/pub/FreeBSD/releases/i386/ISO-IMAGES/8.2/FreeBSD-8.2-RELEASE-i386-dvd1.iso.xz")

There does not seem to be any mirrors where I can download it using BitTorrent.

---

### Post by tech291083 on 2011-07-30
Here is plain OpenBSD download page, 

[ftp://mirror.planetunix.net/pub/OpenBSD/4.9/i386](ftp://mirror.planetunix.net/pub/OpenBSD/4.9/i386)

On this page which one should I download? I want a DVD iso file?

This page is basically one of the mirrors listed here.

[http://www.openbsd.org/ftp.html#http](http://www.openbsd.org/ftp.html#http)

Thanks

---

### Post by boydrice on 2011-07-30
> **tech291083 said:**
> Ok, here is the plain BSD download page. I am going for DVD iso so I think I should go for the 2017993 KB file, right?

[FreeBSD-8.2-RELEASE-i386-dvd1.iso.xz]("ftp://ftp.freebsd.org/pub/FreeBSD/releases/i386/ISO-IMAGES/8.2/FreeBSD-8.2-RELEASE-i386-dvd1.iso.xz")

There does not seem to be any mirrors where I can download it using BitTorrent.

If you have decent internet connection you can also just use the first CD (disc1) or the bootonly iso.  Also I don't know what you like or find interesting about linux or your comfort level at the command line, or your desire to read documentation.  If you are not prepared to follow the handbook [http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/") then stop and try PC-BSD or GhostBSD.

---

### Post by NightwishFan on 2011-07-30
Also, there is Debian GNU/KfreeBSD, which is the GNU userspace with the FreeBSD kernel. I have heard good things about both PC-BSD and Ghost though.
[http://www.debian.org/ports/kfreebsd-gnu/](http://www.debian.org/ports/kfreebsd-gnu/)

---

### Post by tech291083 on 2011-07-30
> **boydrice said:**
> just use the first CD (disc1) or the bootonly iso........ try PC-BSD or GhostBSD.

This is really useful info. Thanks.

Now here is a download page for PC-BSD. As I would love to use BitTorrent to download 32 bit DVD iso, but there are no torrents to be seen here, can you please help, thanks. Here see this Fedora download page, which has torrents and mirrors listed. Something like this would have been really nice.

[http://fedoraproject.org/en/get-fedora-all](http://fedoraproject.org/en/get-fedora-all)

---

### Post by tech291083 on 2011-07-30
Even plain OpenBSD does not seem to have a list of torrents to download from, strange. thanks...

---

### Post by boydrice on 2011-07-30
> **tech291083 said:**
> Even plain OpenBSD does not seem to have a list of torrents to download from, strange. thanks...

The reason for that is most likely do to the small size of the installation media (6.1 mb boot iso or a "hefty" 215 mb install iso).  Think of most BSD installs as similar to an Arch Linux or Debian netinstall.

---

### Post by sffvba[e0rt on 2011-07-30
OpenIndiana... they are continuing where openSolaris ended... the closest to a true Unix system you can have for free...

[http://openindiana.org/](http://openindiana.org/)


404

---

### Post by tech291083 on 2011-07-30
Ok, I have decided to download the latest version of either plain FreeBSD or PC-BSD using torrents as it suits my internet connection most. Now I am not sure which of these two supports both KDE and Gnome. Latest version of PC-BSD is 9 and that of FreeBSD is 8.2 - Please guide me. Thanks..

---

### Post by tech291083 on 2011-07-30
Just found something..

and here for FreeBSD. 

[http://torrents.freebsd.org:8080/](http://torrents.freebsd.org:8080/)

Here are the torrents for PC-BSD

[http://www.gotbsd.net/](http://www.gotbsd.net/)

I hope they work and are reliable. Thanks.

---

### Post by tech291083 on 2011-08-12
Ok, I have two choices now either download the latest version of plain FreeBSD or PC-BSD. My only worry is - which of these 2 supports both KDE and Gnome. Latest version of PC-BSD is 9 and that of FreeBSD is 8.2 - I have read as mentioned by a post in this thread that PC-BSD so far (until the last version 8.2 did not support GNOME, but might change that and start supporting it from version 9, which is still beta I think) Please do reply. Thanks..

---

### Post by TheNosh on 2011-08-12
> **not found said:**
> OpenIndiana... they are continuing where openSolaris ended... the closest to a true Unix system you can have for free...

[http://openindiana.org/](http://openindiana.org/)

404

Oracle still puts out Solaris releases for free, and the development branch (which is what used to be OpenSolaris) is now called Solaris Express. I run it in a VM.

Big bad Oracle didn't kill Solaris; it's still alive and well.e 
> **tech291083 said:**
> Ok, I have two choices now either download the latest version of plain FreeBSD or PC-BSD. My only worry is - which of these 2 supports both KDE and Gnome. Latest version of PC-BSD is 9 and that of FreeBSD is 8.2 - I have read as mentioned by a post in this thread that PC-BSD so far (until the last version 8.2 did not support GNOME, but might change that and start supporting it from version 9, which is still beta I think) Please do reply. Thanks..

PC-BSD 9 is a testing only release so far. Is not expected to be ready for general use until around September.

FreeBSD is by far the most commonly used BSD, so it's the go-to answer for anyone who's asking which one to use. I have a slightly different opinion when it comes to that, though.

I'd go for either PC-BSD or DragonFly BSD. 

PC-BSD is great because it's by far the easiest to use. They simplify program installation and dependence handling through the .pbi installation method which can be used for most common packages.

Dragonfly BSD, while less user friendly seems to be doing the most to advance BSD's capabilities. It's the only BSD I know of to feature a hybrid kernel, and it's the only system as of yet to support the HAMMER filesystem, though HAMMER is largely similar to ZFS.

---

### Post by tech291083 on 2011-08-12
> **TheNosh said:**
> 
PC-BSD 9 is a testing only release so far. Is not expected to be ready for general use until around September.


Ok, then it is better to wait till then. But what is the system requirements like? I have and old but working desktop - 1 GB RAM, 80 GB HDD, 2 GHz CPU. Good enough?

> 
FreeBSD is by far the most commonly used BSD, so it's the go-to answer for anyone who's asking which one to use. 


Ok, But has it got easy interface for me I am trying Unix for the ever time in my life?

> 
PC-BSD is great because it's by far the easiest to use. They simplify program installation and dependence handling through the .pbi installation method which can be used for most common packages.


I also want to download it - PC-BSD, it somehow looked the right choice for a novice like myself.

Thanks a lot for the clarification, makes sense to me now.

---

### Post by TheNosh on 2011-08-12
> **tech291083 said:**
> Ok, then it is better to wait till then. But what is the system requirements like? I have and old but working desktop - 1 GB RAM, 80 GB HDD, 2 GHz CPU. Good enough?

That ought to do fine.

> Ok, But has it got easy interface for me I am trying Unix for the ever time in my life?

I only used it briefly in a virtual machine a few releases ago, but it seemed easy enough. If you're already relatively comfortable using Linux, you shouldn't have any trouble.

---

### Post by kaldor on 2011-08-12
I love FreeBSD. But, if you're trying to set it up like a Linux desktop, it isn't for you.

I learned about how BSD worked by using it on my file server. I became quite familiar with ports, rc.conf, and other things that were different from standard Linux. I forced myself to use only the CLI, and I used it solely via SSH. This is the best way to learn, imo.

Solaris is something to avoid though, in my opinion. I find it to be extremely sluggish on my hardware and it's basically not much different from BSD and Linux. It supports my laptop 100% out of the box, though :)

But overall, become familiar with the "major" *nix systems. Learn about Red Hat Enterprise Linux, FreeBSD, OS X, and Solaris.

---

### Post by TheNosh on 2011-08-12
> **kaldor said:**
> I love FreeBSD. But, if you're trying to set it up like a Linux desktop, it isn't for you.
Desktop use is where PC-BSD comes in.

Some make the argument that that's silly because BSD is designed to be a server OS, but in reality, so was Linux.

> Solaris is something to avoid though, in my opinion. I find it to be extremely sluggish on my hardware and it's basically not much different from BSD and Linux. It supports my laptop 100% out of the box, though :)
Solaris is a bit sluggish, but it isn't too bad. I run Solaris 11 Express on a VM and gave it only a gig of RAM. It's about as speedy as one can expect for most Linux distros in a VM of the same settings.

---

### Post by kaldor on 2011-08-12
> **TheNosh said:**
> Desktop use is where PC-BSD comes in.

Some make the argument that that's silly because BSD is designed to be a server OS, but in reality, so was Linux.

The software and hardware compatibility for Linux is far larger than on any BSD, and Linux is a lot easier to use for desktop users. I ran PC-BSD before, and it's just not "ready". I wouldn't recommend PC-BSD to anyone for use as a desktop. For that reason, I'd suggest using FreeBSD and building it up to what it is needed to be, since it seems to be a learning tool in this case.

---

### Post by TheNosh on 2011-08-12
> **kaldor said:**
> The software and hardware compatibility for Linux is far larger than on any BSD, and Linux is a lot easier to use for desktop users. I ran PC-BSD before, and it's just not "ready". I wouldn't recommend PC-BSD to anyone for use as a desktop. For that reason, I'd suggest using FreeBSD and building it up to what it is needed to be, since it seems to be a learning tool in this case.

PC-BSD is a fine introduction, though. Many people learn Linux starting with simplified distros like Ubuntu or Mint. Would you say that they should all use Gentoo or LFS instead?

PC-BSD is basically just FreeBSD made easier. Perhaps not quite as easy as Ubuntu, but simple enough.

As for compatibility, it should be about the same as FreeBSD. They don't change much.

---

### Post by sffvba[e0rt on 2011-08-13
> **TheNosh said:**
> Oracle still puts out Solaris releases for free, and the development branch (which is what used to be OpenSolaris) is now called Solaris Express. I run it in a VM.

Big bad Oracle didn't kill Solaris; it's still alive and well.e 

[Solaris is not free]("http://arstechnica.com/open-source/news/2010/03/solaris-10-no-longer-free-as-in-beer-now-a-90-day-trial.ars").  And Solaris Express was released as a [preview of the up and coming Solaris 11]("http://www.eweek.com/c/a/IT-Infrastructure/Oracle-Launches-Solaris-11-Express-180625/").

Big bad Oracle didn't kill Solaris, but they did kill OpenSolaris.  Long live OpenIndiana.


404

---

### Post by TheNosh on 2011-08-13
> **not found said:**
> [Solaris is not free]("http://arstechnica.com/open-source/news/2010/03/solaris-10-no-longer-free-as-in-beer-now-a-90-day-trial.ars").  And Solaris Express was released as a [preview of the up and coming Solaris 11]("http://www.eweek.com/c/a/IT-Infrastructure/Oracle-Launches-Solaris-11-Express-180625/").

Big bad Oracle didn't kill Solaris, but they did kill OpenSolaris.  Long live OpenIndiana.


404

Hmm. I can't find anything about this "90 day trial" business in the Solaris license agreement on the download page, or anywhere on Oracle's site. I don't feel like downloading Solaris 10 and waiting 3 months to see if it bugs me for money, so I suppose I'll abandon that point of the debate.

However, if you would like to find me confirmation of this 90-day trial period from Oracle rather than a tech news site, it would be greatly appreciated. Obviously you don't have to, though.

As for Solaris Express not being OpenSolaris, yes it is. They've just closed the development process, so leaving "open" in the name didn't make sense. Yes, it is a preview release of Solaris 11, but OpenSolaris was the same thing. Features got tested in OpenSolaris and then Implemented into Solaris for the next release.

---

### Post by kaldor on 2011-08-13
> **TheNosh said:**
> PC-BSD is a fine introduction, though. Many people learn Linux starting with simplified distros like Ubuntu or Mint. Would you say that they should all use Gentoo or LFS instead?

PC-BSD is basically just FreeBSD made easier. Perhaps not quite as easy as Ubuntu, but simple enough.

As for compatibility, it should be about the same as FreeBSD. They don't change much.

PC-BSD just feels like a broken experience to me. It has some non-standard BSD stuff included, and I think that if you really want to learn about *nix and *BSD, you should do it the traditional way. It's not hard to do, either. It didn't take me long to follow the (simply awesome) FreeBSD documentation and set it up exactly how I wanted. Gentoo and LFS aren't really good examples. If you install FreeBSD (very fast to do) and then learn how ports or pkg_add works (also pretty easy and fast) you can have an OS up and running pretty quickly, unlike Gentoo/Arch/LFS/Slackware/etc. It gets you into the loop of using a BSD OS a bit quicker than just using FreeBSD with KDE + extras.

You also need to remember the audience of BSD. Ubuntu is aimed toward the mainstream, while PC-BSD is still very much an early adopter OS. If someone is asking about wanting to try UNIX, why would PC-BSD be a good idea? I just think that learning from the ground up on BSD would be a much more rewarding and helpful experience. It's not a huge task to accomplish.

The compatibility should be identical to FreeBSD, yes. But that isn't what I meant to refer to.

These are all just my opinions, though. I'm not trying to state any facts. Just giving my thoughts on the subject, since I went through the whole BSD phase a few months back :)

---

### Post by tech291083 on 2011-08-16
> **kaldor said:**
> Linux is a lot easier to use for desktop users. I ran PC-BSD before, and it's just not "ready". I wouldn't recommend PC-BSD to anyone for use as a desktop. For that reason, I'd suggest using FreeBSD and building it up to what it is needed to be, since it seems to be a learning tool in this case.

This is what exactly I would have liked as an ideal anwser to my query considering my enthusiam about Unix, but lack of experience with it.

---

### Post by tech291083 on 2011-08-16
> **TheNosh said:**
> Desktop use is where PC-BSD comes in.

Some make the argument that that's silly because BSD is designed to be a server OS, but in reality, so was Linux.


Yes, I want a desktop friendly version of Unix.

---

### Post by tech291083 on 2011-08-16
> **TheNosh said:**
> PC-BSD is basically just FreeBSD made easier. Perhaps not quite as easy as Ubuntu, but simple enough.



I am really happy to know that. Thanks

---

### Post by tech291083 on 2011-08-16
> **kaldor said:**
> 
 if you really want to learn about *nix and *BSD, you should do it the traditional way. It's not hard to do, either. It didn't take me long to follow the FreeBSD documentation and set it up exactly how I wanted. If you install FreeBSD and then learn how ports or pkg_add works you can have an OS up and running.


I am going to consider this as well, my lack of experience with Unix- FreeBSD frightens a lot. Thanks.

---

