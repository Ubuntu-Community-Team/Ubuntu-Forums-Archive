---
title: "BSD Talk"
date: 2005-04-27
forum: BSD
---

### Post by poofyhairguy on 2005-04-27
Before I say anything I want to state that I hope no one gets the temptation to troll in this thread. I want to read the opinions of the knowledgeable Ubuntu Community without challenging any egos.

Now that Debian is going to take on a BSD branch, I have began to wonder about BSD.  I once tried the FreeBSD live CD in late 2004- FreeSBIE- but it worked about as well as dirt works in a car engine on my computer. Because the Live CD didn't work, and I have not touched BSD again. Didn't have the hard disk to do more.

But soon I'll get a bigger hard disk which I plan to partition in many ways. I want to give BSD another shot.

My questions are: What are the unique things about BSD? Are the different forms of BSD like distros in Linux? Is there a BSD you like more than others? 

Again, please no anti-BSD trolls. If you dislike BSD, you can say why but please do in a mature manner. Thanks in advance.

---

### Post by TravisNewman on 2005-04-27
There are a few BSD flavors, but nowhere near as many as Linux. FreeBSD is my favorite because of the ports system (what Gentoo's portage is based on). NetBSD and OpenBSD are good too from what I've seen. I haven't had as much experience with BSD as I have with Linux, so some things still don't make sense.

I'd also suggest trying out Solaris while you're at it. Solaris and BSD are similar in the way things work, but not identical.

---

### Post by poofyhairguy on 2005-04-27
[QUOTE=panickedthumb]There are a few BSD flavors, but nowhere near as many as Linux. FreeBSD is my favorite because of the ports system (what Gentoo's portage is based on). NetBSD and OpenBSD are good too from what I've seen. I haven't had as much experience with BSD as I have with Linux, so some things still don't make sense.
[/QUOTE]

So, this FreeBSD has something liek apt-get for software. That is needed by me.


[QUOTE=panickedthumb]I'd also suggest trying out Solaris while you're at it. Solaris and BSD are similar in the way things work, but not identical.[/QUOTE]

I will, but it won't get a spot forever.

---

### Post by TravisNewman on 2005-04-27
Basically, from what I remember, you download the ports tree. Say you want to install gaim. You would do something like this.

cd /path/to/ports/tree/internet/gaim
make install

and it would check dependencies and install it.

---

### Post by poofyhairguy on 2005-04-27
[QUOTE=panickedthumb]Basically, from what I remember, you download the ports tree. Say you want to install gaim. You would do something like this.

cd /path/to/ports/tree/internet/gaim
make install

and it would check dependencies and install it.[/QUOTE]

Are there binary packages?

---

### Post by TravisNewman on 2005-04-27
that I'm not sure of. Never tried to find out, just used the sources. I can only assume that there are, lots of people won't have the time or patience to use it if there aren't.

---

### Post by defkewl on 2005-04-27
BSD are nice. Each flavor has a focus. 

Open focused on security
Free focused on stability
Net focused on multi-platform

I think each BSD has their own kernel none-like Linux.

---

### Post by kahping on 2005-04-27
[QUOTE=panickedthumb]that I'm not sure of. Never tried to find out, just used the sources. I can only assume that there are, lots of people won't have the time or patience to use it if there aren't.[/QUOTE]

i can confirm that they do.

instead of 'make install', you just 'pkgsrc <package_name>' and it will check and download dependancies, then install precompiled binaries instead of compile from source.

kahping

---

### Post by Nob on 2005-04-27
nope, in bsd there are no binaries. only source files.
portage tree is same as debian, and you get them from server with pkg_add if i recall...
in that way, you download source file, configure it, compile and install it automatically.

bsd is better than linux coz it has the most stable kernel of them all. supports allmost all hardware [as 2.6 kernel in linux], and has much better stability even of 2.4 kernels on linux
what is complicated is installation.
on first you install base system of about 300mb... fter that you have to compile everything.

so you have to be linux master to get over bsd, i tried it, but i realised that its not the time yet...

so good luck!

---

### Post by kahping on 2005-04-27
really!? from the documentation it sure sounded like there are binaries available to me. of course, if you want the latest versions af packages, most likely binaries aren't available(yet).

o yea, thanks for the correction. i mistakenly said 'pkgsrc <package_name>' when it's supposed to be 'pkg_add <package_name>'. my mistake :-P

kahping

---

### Post by Knome_fan on 2005-04-27
I'm no BSD expert, but I'm pretty sure that there are binary packages available.

Anyway, I just stumbled upon the following which might interest you, a userfriendly FreeBSD:
[http://www.pcbsd.org/](http://www.pcbsd.org/)

---

### Post by el000 on 2005-04-27
I tried FreeBSD about 6 months ago. There are two ways to install new packages: The ports system (source) and the packages system (binaries). However, there weren't as many binaries as in debian. 

Something that I didn't like was that you often had to edit text files in order to get things to work (e.g. sound card, ppp). Yesterday I read about a new BSD distribution, [PC-BSD](http://www.pcbsd.org) , which is based on FreeBSD and aims to be easy to install and use. It is their first release and I am not sure how ready it is.

Anyway, coming back to FreeBSD, one of the great things is that it has fantastic documentation (handbook). So, even though you have to edit configuration files you can find detailed instructions on how to do it.

Hope this helps.

---

### Post by HungSquirrel on 2005-04-27
I hated FreeBSD and loved OpenBSD.  However, I don't think OpenBSD makes a great desktop distro unless you're paranoid about security.  It ran slow as molasses in X, but it installs in secure by default mode and makes a great server, router, or firewall.  YMMV.

If I recall correctly, all three major BSDs have good binary package management as well as ports trees (FreeBSD has the most ports, being the largest BSD distro).  If you want to do things the Gentoo way (except without all the speed optimizations), you can use ports.  If you want to do things the Debian way, do pkg_add url_to_package, and it will grab the package and all deps and handle installation for you.

FreeBSD's install disc has lots of packages already on it.  With OpenBSD, you have to boot from a floppy and do an FTP install unless you want to buy your own CD.  The FreeBSD install is much easier than the OpenBSD install.  When installing either distro, make sure you understand what you are doing when you come to the disk slicing/partitioning.  The terminology used is very different, as are the device names.  I'd suggest printing out the install instructions.

---

### Post by TravisNewman on 2005-04-27
YMMV? Your mother married Vernon? Yes, my miata vooms? You're my modern vampire? 
[quote=The forum rules]...use as few acronyms as possible...[/quote];)

Anyway, yes yes be very careful when partitioning. What we call partitions are called slices in BSD/Solaris/etc, and partitions are what we might call virtual partitions, if such a thing existed in Linux-- essentially you can have 4 slices, and you partition those slices. Kinda weird, yes. And forget /dev/hda4, /dev/fd0-- there's a whole new terminology there too.

---

### Post by az on 2005-04-27
"Now that Debian is going to take on a BSD branch, I have began to wonder about BSD. I once tried the FreeBSD live CD in late 2004- FreeSBIE- but it worked about as well as dirt works in a car engine on my computer. Because the Live CD didn't work, and I have not touched BSD again. Didn't have the hard disk to do more.


My questions are: What are the unique things about BSD? Are the different forms of BSD like distros in Linux? Is there a BSD you like more than others? "

BSD, Solaris and linux are all unix operating systems.

BSD supports a lot of hardware, but linux has a much bigger home user base.  That means that there is a much better chance your wireless card or printer will work in linux than in BSD.

They each hev their own kernel to handle the unix basics: memory, devices, etc.  The devices have different names, but everything is pretty much unix.  On top of the kernel you need tools.

Linux uses GNU.  You get the GNU coreutilities:

"This package contains the essential basic system utilities. 

Specifically, this package includes: basename cat chgrp chmod chown chroot cksum comm cp csplit cut date dd df dir dircolors dirname du echo env expand expr factor false fmt fold groups head hostid id install join link ln logname ls md5sum mkdir mkfifo mknod mv nice nl nohup od paste pathchk pinky pr printenv printf ptx pwd readlink rm rmdir sha1sum seq shred sleep sort split stat stty sum sync tac tail tee test touch tr true tsort tty uname unexpand uniq unlink users vdir wc who whoami yes"

On BSD, you may use the bsd core utilities.  They may have slightly different functionality, but they should all work the same way in principle.  On Solaris, you probably have a proprietary implementation of these tools.

On top of that (along with the gnu developmental tools (gnu make, GCC, etc...)) you get the higher level package management stuff.  It may be apt, rpm.  It may be ports, or some other system.  It may be a proprietary system.

But, the point is that there are certain unix standards to respect.  You should be able to compile x.org and gnome from source on solaris and run it just as it would run on linux or BSD.

Now, if you are using GNU BSD, You will have a BSD kernel, but with all the gnu tools - and that includes apt.  Probably the only thing you would notice to be different would be that the deviceas have different names.

---

### Post by TravisNewman on 2005-04-27
[i]" BSD, Solaris and linux are all unix operating systems."

[/i]Depends on who you ask ;) Solaris, and BSD, among others, are technically UNIX, but Linux is technically a UNIX clone. Splitting hairs I know. I've used a few other UNIX systems, and they all seem to function in close to the same way, but Linux is kinda the outlier that doesn't (as far as filesystem structure and device names go, anyway)

---

### Post by Nob on 2005-04-27
well my friend uses freeBSD for allmsot 2 years, and i'm preety sure that even when you grab packages via pkg_add, you get source, and system automaticaly does the thing [install dependencies, etc]
maybe i'm wrong...

---

### Post by jerome bettis on 2005-04-27
i was curious myself so i went and tried installing it.

it's installed, i can mess around a little bit but most of my hardware (network!) doesn't work yet.  i don't really have the time right now to mess with it too much so it will probably just sit around for a month or so until i get motivated.

---

### Post by Quest-Master on 2005-04-27
Hehe, I had the same experience as you. Popped in FreeSBIE, and none of the options (XFCE, Flux, Terminal) worked at all. Haven't touched BSD since.

---

### Post by HungSquirrel on 2005-04-27
I loved FreeSBIE.  X, audio, and video all worked like a charm.  Unfortunately, its install to disk option does not install FreeSBIE to the hard drive, but a sort of stripped down FreeBSD.  I wish it installed the live FreeSBIE straight to the disk so I wouldn't have to fool with getting sound working, which seems to be a pain on BSDs.

FreeSBIE could have also used a bit of professional touch-up work.  For example, upon loading The GIMP, you see an error that it can't write the tile cache or something similar to the disk.  (Duh, /home is on a read-only filesystem!)  Had the devs been smart they would have found one of a number of ways to prevent the error from popping up.

---

### Post by Nob on 2005-04-28
if u use FreeSBIE, dont install it on hard drive, use it only as live distro..

---

### Post by poofyhairguy on 2005-04-28
[QUOTE=Nob]if u use FreeSBIE, dont install it on hard drive, use it only as live distro..[/QUOTE]


Ok. What BSD is good for a harddrive install?

---

### Post by HungSquirrel on 2005-04-28
Any of them except FreeSBIE.  The install to disc option on the live distro sucks.

---

### Post by dataw0lf on 2005-04-28
I'm a bit biased on this subject: I love FreeBSD with all of my heart.  However, FreeBSD (and the other flavors of BSD) can be quite a change for Linux users.  I certainly don't advocate using FreeBSD as a desktop (in the same vein that I don't advocate Ubuntu as a server base), but, if you're willing to put in the time, learning FreeBSD can be extremely beneficial and rewarding.  

The Gentoo portage system was indeed inspired by FreeBSD, but they certainly don't do it nearly as efficiently, or achieve the other remarkable achievements of FreeBSD: incredible stability, maturity, and overall just some great tools (pf compared to iptables springs rapidly to mind, especially from a 'general user's' point of view).  FreeBSD's robustness (especially under incredible pressure) speaks highly of the engineers who've designed it.  If you've ever ran some enterprise Linux servers under heavy load, you'd probably appreciate BSD infinitely more. 

A good thing to remember regarding Linux versus BSD discussions is this:  Linux is on the cutting edge of hardware and software.  The Linux kernel accepts patches and addons that even the wildest BSD developer wouldn't touch with a 10 foot pole.  This is one of the major reasons why Linux has gained such popularity in the desktop arena: it (generally) supports all your cool little toys you want to plug into your box.  

One of the most confusing aspects is probably the switch from SysV based runlevels (which most Linux distros use) to BSD based runlevels.  However, once you become acclimated to that, you see the enormous benefits (and increase in boot and shutdown processes) from the BSD based runlevel versus SysV.

As far as panickedthumb's endorsement of Solaris, all I can say is: DON'T DO IT! :|  Seriously, I've worked both professionally and personally with a number of flavors of Unixes, but Solaris is probably the worst, by far, that I've ever used.  Why does Sun always feel the need to break things?

You might be able to attribute that to my intense hatred of Sun though ;)

---

### Post by TravisNewman on 2005-04-28
Heh. I didn't dislike Solaris, but it DEFINITELY wasn't what FreeBSD is. Hopefully in the coming years Solaris will improve greatly, since they're opening the project. I think Solaris has a LOT of good ideas, and they're implemented mostly well, but it could use some work. The thing that gets me about Solaris-- installation time: I don't THINK the installer is compiling everything, but you'd think it was. Took a good two and a half hours from inserting the first cd to removing the last.

---

### Post by DJ_Max on 2005-04-28
> **panickedthumb][i]" BSD, Solaris and linux are all unix operating systems."

[/i]Depends on who you ask  said:**
> 
 BSD shares code with the orginal Unix OS developed by AT&T/Bell. Linux is based on some Unix ideas.

All of the BSD's provide pre-built binaries as well as source.

I've read tons of BSD related docs, and will be installing NetBSD on my iMac in a few days, I fine the system more logical then most. Not only with the package system, but the way the kernel and most utilities are in the base system, which doesn't really exsist in a Linux environment.

[QUOTE]Linux is on the cutting edge of hardware and software. The Linux kernel accepts patches and addons that even the wildest BSD developer wouldn't touch with a 10 foot pole. 
BSD waiting for proper testing isn't necessarily a bad thing. Most common hardware works the same as Linux, only a few oddball hardware doesn't get support as quick as Linux, and for good reason..

---

### Post by crazybill on 2005-04-28
I want to try to end some confusion about UNIX/Linux/BSD and give you some of my experience... which is new to Ubuntu Linux .. but old with BSD...  well, old from a modern computing sense.

**_The "Which is more UNIX: BSD or LINUX" Question_**
From a purely historic standpoint, both BSD and LINUX are derived from the Bell Lab's  first UNICS (Sept 1969) which was soon renamed UNIX Time-sharing system).  The "CS" (Computing Service) part of the acronym became "X";  CS=X!  The UNIX operating system was designed to let a number of programmers access a computer at the same time and share its resources. It was made by programmers for programmers, allowing multi-tasking and multi-users, with portability.  There was only one flavor of UNIX (UNIX Time-Sharing System) until around 1974, when it started to splinter into branches. BSD  branched off in March 1978 when AT&T relinquished its UNIX copywrite to University of California Berkley who distributed it open source under "Berkley Software Distribution" : BSD.

To be a UNIX operating system, there must be a historical link in development .. which there is for the distributions that call themselves Linux, for those that call themselves BSD, and for some (like Solaris and Mac) that don't use that nomenclature at all.  The UNIX system and any present day distribution that calls itself "UNIX" or "UNIX-like" must be  functionally organized at three levels:
**    1.  The kernel, scheduling tasks and managing storage;**
**    2.  The shell, connecting and interpreting users' commands, calling programs from memory, and executing them.**
**    3.  The tools and applications, usually simple and sweet, that offer greater function to the operating system**

For these reasons Ubuntu Linux is indeed a UNIX operating system, as is OpenBSD, FreeBSD. These are all examples of  open source operating system with kernel, shell, and applicable tools that fit the definition above.  Too, historically, its kernel-shell-core tools were derived from the original UNIX and they still share many common shells, tools, and kernel characteristics.

The arguments that  say BSD is more UNIX and Linux is less UNIX is, to my eyes,  fairly bogus. First, the genetic tree from UNICs to BSD or LINUX is more of a spider web than a tree, due to sharing of ideas throughout concerning the kernel, sharing the same shells, and sharing most of the same tools. Secondly, whereas BSD separated from "UNIX Time-sharing system" (the base of the genetic tree) in March 1978. Linux branched from the same trunk in 1984, so in that regard is "more UNIX". There have been connects and disconnects since that time between BSD distributions and Linux distributions.

Ubuntu Linux, openBSD, FreeBSD are all UNIX operating sytems.

_**THE DERIVATIONS (Unix Family Tree/Web for Ubuntu and BSD)**_

There was one UNIX from 1969- 1973 (UNIX Time Sharing System). Around 1974   MERT and PWB UNIX broke off from "UNIX time sharing system". Thus, in 1974, there were 3 flavors.  Eventually, AT&T gave up its rights to UNIX and University of California in Berkley started being the major guardian -- hense BSD (Berkley Software Distribution).  BSD was born in March, 1978. There was 1BSD in '78, 2BSD in '79... until the 4BSD kernel was born around 1980 and they started naming it 4.0 and incrementing by tenths. Quite a few flavors of BSD started branching off the 4.x BSD kernels. 

NetBSD  is the oldest of the BSDs keeping their name. FreeBSD started in December 1993 from the 386BSD project.  Open BSD branched off of NetBSD in October 1995. (I started using it in '97). One of the derivatives of UNIX came to be known as GNU. GNU started in the 70s. The Debian group branched off of that in 2000. Ubuntu/Kubuntu branched from that. With respect to the Linux 2.6.10 kernel of Ubuntu/Kubuntu... it actuall came from UNIX through Minix to Linux, with an infusion of BSD4.x to Irix to Linux.  Actually if you tried to plot all of the UNIX/BSD/LINUX flavors, the genetic diagram would not really look like a genetic "tree" but more like a genetic "spiderweb". One branch would grow into another or at least share ideas, tools, shells with each other. In short UNIX, LINUX, and BSD are joined at the hip, shoulder and feet!

_openBSD:_
UNICS ('69) --> UNIX Time-sharing System (1st - 6th ed.) --> 1BSD -->2 BSD--- etc through BSD 4.x--> netBSD --> openBSD

_freeBSD_ 
UNICS ('69) --> UNIX Time-sharing System (1st - 6th ed.) --> 1BSD -->2 BSD--- etc through BSD 4.x--> 386tBSD --> freeBSD

_Ubuntu/Kubuntu Linux  (ref Debian) _ 
UNICS ('69) --> UNIX Time-sharing System (1st - 9th ed.) -->GNU(Trix)GNU/Herd--> Debian GNU/Herd----------> Debian GNU--> Ubuntu Linux 

_Ubuntu/Kubuntu Linux (ref Linux 2.6.10 kernel) _ 
UNICS ('69) --> UNIX Time-sharing System (1st - 7th ed.**) --> Minix -->Linux 0.1----------> Linux 2.6.10 --> Ubuntu Linux    (** there is also a split off into BSD 4.x, then a branch to IRIX and then to Linux... so it is really a web rather than an nice tree)

_**My Background experience with BSD  (large)  AND LINUX (small)**_
First, I have been using FreeBSD since 1995 and openBSD since 1997.  I run [http://www.cvc.org](http://www.cvc.org), [http://home.cvc.org](http://home.cvc.org) and [http://www.drennon.org](http://www.drennon.org) and a couple more in those domains on openBSD since 1997 and through this year on the same circa 1995 hardware, with no problems, no crashes. Because we have over 7,000,000 visitors to the web servers now (compared to only 3000 the first year), and because a power supply failed, I upgraded the older servers this year to newer hardware.  I mentioned that information  to give you an idea of BSD's stability and security.   I still run a couple of email servers with freeBSD, including one that has been running without crashing since 1995!  Most of my LAN and private WAN servers (there are 18 of them) are openBSD.  For servers, routers, etc,  BSD is great. I am using some openBSD machines that are quite old but still doing a great job and they never never never stop ticking.  I do use some Windows  on my LANs but only because of software restrictions that require Windows. I have one NT server and two Win2000 servers -- but hope to eventually get rid of them. I have a couple of servers that are Linux: Ubuntu Linux.. and thus far, they have been trouble free.

I have tried performance tests of various flavors of BSD with Linux and openBSD has always come up the winner. OpenBSD is so darned easy to tweak.  OpenBSD, too, is extremely secure. As a webserver. it just can't be beat... and the root of the apache webserver is different than the root of the computer. Packages and ports are not hard to deal with, once you get use to it. For a server, that is going to have multiple users logged on at a time, doing mulitple tasks, openBSD is wonderful.

FreeBSD is not bad, either. In truth, FreeBSD is downright awesome.  However, with respect to how I tweak things, openBSD out performed FreeBSD in every test I have done since 1997, For public IP computers and even private LAN computers with confidential info on them, FreeBSD has given way to openBSD. I started with FreeBSD, mind you, so have a love for it, but it is giving way to open BSD.

I have tried x-windows type desktops with openBSD and freeBSD, but always rejected them. For servers, they are great, but not for workstations or standalone computers, in my estimation.  There are presently three main open source UNIX branches that call themselves "BSD": netBSD, freeBSD (the largest), and openBSD. openBSD broke branched off from netBSD.  To be fair, I have never tried netBSD.

Apple, by the way, is a commercial BSD. 

Annually, I have been going through the ritutal of trying various flavors of Linux (there are about 300 flavors of Linux!) , but performance was never as good as the BSDs, even though the desktop was better... but I was still not willing to give up Windows for  most desktop applications... until this year when I discovered Ubuntu and then Kubuntu.





_My recommendation:_

**openBSD** -- the best there is for security and tweaking a limited machine to behave like a powerful machine. The hardship here is the front-end setup... but after that, it is problem free.   The packages and ports are not that hard to set up once you get use to it.  I do not recommend it for a desktop. It is the best of the best for servers. I have always made my own CDs for setup and given them to friends with step by step directions. I know many folks that I initially set up using openBSD that still use it and love it.

**freeBSD** -- easier to setup than openBSD and the most popular and largest BSD. It also makes a good server. I am still using a machine that I have had since 1995 with freeBSD and it is still cooking. Though the perfomance always is killed by openBSD on a head to head test, it is almost as good. There are more packages and more people using it than openBSD, and thus more help available.


**Ubuntu/Kubuntu Linux** -- I have used Ubuntu Linux for less than a year and Kubuntu for less than a week. I have tested a lot of Linux flavors... but do not want to dish any... just to say I found Ubuntu/Kubuntu to be, by far the best. It makes the first really good workstation/home computer that I have seen. Although, I love Ubuntu, I think that I am going to like Kubuntu even better because of the KDE desktop over Gnome. However, I have not used it enough yet to really say... it is only my strong hunch at this point.  I would and am using Ubuntu as servers as well as stand-alone machines... because it is, afterall, a UNIX machine and they are great as remote servers... MUCH MUCH MUCH better than Windows. The ease of setup and making quick changes is a big plus, even though the performance is not quite as good as the BSDs. Today's computers though  are mcuh much better than when I started out.. so a Pentium IV with 512 MB of RAM is making a better server than an Open BSD on a Pentium II 200 MHz machine with 64 MB of RAM!... and it was quicker and easier to set up.

Over 90% of the tools I use on openBSD and freeBSD, I use in the remote terminal for Ubuntu and Kubuntu.... because after all, they are all UNIX.

I hope this helps.

---

### Post by BWF89 on 2005-04-28
I heard that one of the BSD's is working on an apt-get like program for it.

If I knew more about computers I'd use BSD over Linux anyday. Especially since BSD can run and Linux program (or so I've heard).

---

### Post by HungSquirrel on 2005-04-28
> I heard that one of the BSD's is working on an apt-get like program for it.
ME WANT

---

### Post by TravisNewman on 2005-04-29
I thought BDS stood for Berkely STANDARD Distribution. But that's a minor detail. Good history lesson bro!

---

### Post by az on 2005-04-29
That is a great description.  Thank you.

"Ubuntu/Kubuntu Linux (ref Debian) 
UNICS ('69) --> UNIX Time-sharing System (1st - 9th ed.) -->GNU(Trix)GNU/Herd--> Debian GNU/Herd----------> Debian GNU--> Ubuntu Linux 

Ubuntu/Kubuntu Linux (ref Linux 2.6.10 kernel) 
UNICS ('69) --> UNIX Time-sharing System (1st - 7th ed.**) --> Minix -->Linux 0.1----------> Linux 2.6.10 --> Ubuntu Linux (** there is also a split off into BSD 4.x, then a branch to IRIX and then to Linux... so it is really a web rather than an nice tree)"

I do not understand.  There is a distiction (that is quite important) between GNU the kernel (hurd) and GNU the OS (the tools).  There is no difference between the tools used in debian GNU/linux and debian GNU/Hurd.

So should it not be:

UNICS ('69) --> UNIX Time-sharing System (1st - 9th ed.) -->GNU(Trix)GNU/Herd--> Debian GNU/Herd----------> Debian **GNU/linux**--> Ubuntu Linux 



Either I am wrong or misunderstanding you, or perhaps it is just an oversight and it would seem that I am picking nits.

---

### Post by TravisNewman on 2005-04-29
" Either I am wrong or misunderstanding you, or perhaps it is just an oversight and it would seem that I am picking nits."
I didn't notice that. But did Debian start off with Hurd? I thought it started with the linux kernel and added hurd later? Ah, it's confusing ;)

---

### Post by az on 2005-04-29
GNU started off as being both the tools and the Hurd.

A monolythic kernel is more practical and so linux took off.  Linus Torvalds used the GPL and GNU (tools) to develop the linux kernel.

He even said originally that he did not expect linux to be "as big as GNU"  He meant that the Hurd was a more ambitious project at the time.

In this context, Debian is just a bunch of people.  They used whatever worked.  This is why Brandon Robinson correctly refers to Debian (the Operating system) as Debian GNU/linux.

---

### Post by Nob on 2005-04-29
[QUOTE=poofyhairguy]Ok. What BSD is good for a harddrive install?[/QUOTE]
 FreeBSD, OpenBSD, PCBSD or DragonflyBSD ;)
no live distros..

---

### Post by TravisNewman on 2005-04-29
[QUOTE=azz]GNU started off as being both the tools and the Hurd.[/quote]
Yeah I did know that, but I didn't think Debian started with Gnu tools AND the hurd, I thought they started with Gnu tools and Linux kernel. And yes, Debian GNU/Linux is the correct term-- when you get right down to it <any distro> GNU/Linux is the correct term. The kernel is fantastic, but you couldn't do jack with it without the GNU tools.

---

### Post by az on 2005-04-29
[QUOTE=panickedthumb]Yeah I did know that, but I didn't think Debian started with Gnu tools AND the hurd, I thought they started with Gnu tools and Linux kernel. And yes, Debian GNU/Linux is the correct term-- when you get right down to it <any distro> GNU/Linux is the correct term. The kernel is fantastic, but you couldn't do jack with it without the GNU tools.[/QUOTE]

Ah!  Yes!  I am sorry.  You are right.  Debian started with a linux kernel.

---

### Post by NaplesBill on 2005-05-04
I installed the latest 0.6 Beta of PCBSD on my Thinkpad T41 and all I can say is WOW!  This thing smokes.  I can't believe how responsive this system is.  Menus, apps, everything pops and snaps instantly.  I'm very impressed.

I have tried to load a couple different BSD distros in the past and it was always more of a headache than I cared to deal with.  The PCBSD install took about 20 minutes and it has worked flawlessly since.  This is with a beta product?

I guess the only downside is that there aren't a lot of packages just yet.  All in all I have to say this may give Ubuntu a run for it's money(oh yeah, they're both free)!

---

### Post by TravisNewman on 2005-05-04
There's a Linux compatibilty layer in BSD that will let you run Linux apps. I haven't seen any problems with it in my limited experience with it

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=crazybill]
I hope this helps.[/QUOTE]

More than you can imagine. I wish you would (or would give me permission to) add that to Wikipedia. Thats great....

---

### Post by deviant03 on 2005-05-13
[QUOTE=poofyhairguy]More than you can imagine. I wish you would (or would give me permission to) add that to Wikipedia. Thats great....[/QUOTE]

Yeah man, that is one heck of a post crazybill. Exactly the type of info I was looking for.

---

### Post by ice60 on 2006-05-16
hi, i really want to try a BSD live cd, is there one which is easy to make? i'm worried about downloading an iso then not being able to configure some BSD startup scripts or something which will take along time working out how to work because you need to know alot about BSD which i don't :( 

do you have any ideas? thanks.

---

### Post by Ramon on 2006-05-16
[http://distrowatch.com/table.php?distribution=freesbie](http://distrowatch.com/table.php?distribution=freesbie)
try this for example ??

---

### Post by ice60 on 2006-05-16
[QUOTE=Ramon][http://distrowatch.com/table.php?distribution=freesbie](http://distrowatch.com/table.php?distribution=freesbie)
try this for example ??[/QUOTE]
hi, i did find afew 'distros' earlier but this is what put me off
[http://livecd.sourceforge.net/](http://livecd.sourceforge.net/)
>  allow one to [color=red]generate[/color] their own custom FreeBSD Live CDs i'm just not sure i'm able to generate anything BSD :rolleyes: 

actually, freesbie made me think of trying a live BSD in the first place because i heard it mentioned on an old [tllts](http://tllts.info/), i hadn't thought of using one, i just planed to do an install in the next month or so.

have you, or anyone, tried freesbie? is it the same as making a Linux iso? or does it need to be configured? thanks :) 

this is from the Distrowatch link
>  FreeSBIE project goals are mainly two: to develop a suite of programs to be used to create your own CD, with all the personalisations you like :-|

---

### Post by ice60 on 2006-05-16
i want to try either FreeSBIE or OliveBSD
[http://g.paderni.free.fr/olivebsd/](http://g.paderni.free.fr/olivebsd/)

has anyone ever used either one? is it the same process as a Linux live cd? or do they need to be configured at boot? thanks

---

### Post by mips on 2006-05-16
Another option is to install the VMware player or server. Then download one of the many ready made images of bsd and run it as a virtual pc from within linux. I downloaded everything last night and just have to figure out how to install vmware server so I can use the freebsd & openbsd images I got via links from the vmware site. 

Once I'm familair with them I will try a install on a clean HD. I had a look at the bsd partitioner last night and it confused the hell outa me, so I did not install it on my main drive with existing partitions. Not taking a chance.

[http://www.vmware.com/](http://www.vmware.com/)
[http://www.vmware.com/vmtn/appliances/directory/](http://www.vmware.com/vmtn/appliances/directory/)

In my opinion a much better alternative to a livecd as you still have full acces to ubuntu while running another os in a virtual machine.

---

### Post by slimdog360 on 2006-07-05
Ive been looking at it and other BSD OSs in general. Im not planning on changing over I just want to find out more about it. Is it any good? Who is it for? that sort  of thing.
thanks

---

### Post by SpEcIeS on 2006-07-05
In the past I have used FreeBSD and enjoyed it. A little different, but basically the same. More of a Unix.

---

### Post by matthew on 2006-07-05
It's quite good--incredibly stable. I would not recommend it for beginners in the Unix/Linux world, though. However, you can do with it just about anything that you can do with a linux distro. The downside is that ther is less hardware supported and it takes longer for new hardware to be added in. The upside is incredible security and stability. I would recommend it for servers primarily, but not exclusively.

Note: I have Free BSD installed under VMWare just to play with/test it. I have found it to be very impressive.

---

### Post by atoponce on 2006-07-05
[quote=slimdog360]Ive been looking at it and other BSD OSs in general. Im not planning on changing over I just want to find out more about it. Is it any good? Who is it for? that sort  of thing.
thanks[/quote] I have played with FreeBSD, and the first thing I noticed was the serious lack of software compared to Debian/Ubuntu.  It wasn't long before I uninstalled it.  However, it was rock solid, quick, and overall, enjoyable.  Don't know if I would recommend it to a first time user though.

---

### Post by FredB on 2006-07-06
FreeBSD is a great OS. But a little too rough for me. Even if I do love unix based system, BSD is too "square" for me.

Lack of support for some tools is for me a blocker. BSDs are great for servers, but for desktop user ?!

---

### Post by hizaguchi on 2006-07-06
I used it for a little while.  It was really quick and it had better support for suspend with my laptop (Inspiron 4150) while in X, but I got tired of compiling software really soon.  Yeah, there are packages, but they are ususally a version or two behind the ports so doing "portupgrade -a -P" (equivalent to apt-get dist-upgrade) usually means a couple hours of compiling.  I don't have the patience for that.  Plus there's alot of re-learning to do, and I don't feel like I know enough about Linux to move on to learning something else so soon.

---

### Post by nocturn on 2006-07-06
FreeBSD 4.x was rock solid and in that time much faster then Linux (2.4 kernels).

With the rise of the 2.6 kernel and FreeBSD 5, the difference got a lot less and the 5.x series was a disappointment after 4.x.  In addition, FreeBSD lacked USB2 and FireWire support long after they were stable in Linux.

Basicly, it's a good OS, but hardware support is where Linux was 5 years ago and the performance difference is nearly gone AFAIK.

---

### Post by FredB on 2006-07-06
It seems 6.x branch is better than 5.x for hardware. But I don't like the "too clean" point of view of BSD.

Maybe I passed to much on linux those past years ? ;)

---

### Post by K.Mandla on 2006-07-08
I tried PC-BSD for a short while, but I couldn't get into it. I know there are some folks that are quite enthused by it.

---

### Post by FredB on 2006-07-09
PC BSD is not that bad. It is too closed for software installation. It is too windows-like for that point.

But some people like that, so...

---

### Post by Protostar on 2006-07-10
I've used it. I tried it out with my laptop and getting the XServer set up was hard as hell. I think that had something to do with my ATI graphics chipset and the weird resolution the laptop used (1440x900). Once I got the DE up (I was using KDE then) I managed to get Opera installed. I also managed to get Kopete configured with my AIM account. Beyond that, I don't remember doing much else except reinstalling Ubuntu Breezy. I think I'll try it again once I get a new HD for my testing computer. I'm not one to give up on a challenge.:p

---

### Post by richbarna on 2006-07-12
For some reason bsd acts like windows, it doesn't like to be booted from inside  an extended partition, I played around for quite a while before finding this information (lack of reading on my part). I, like others, found the speed and stability impressive, but although I don't like bloated distros, found bsd lacking in desktop software. After working hard to get it up and running, it got replaced within a week by Berry Linux. I am gradually working my way through different Linux distros, on a scale from easy to hard, but bsd was a bit too much for me.
I will stick with linux distros for the moment. (there's plenty of them :))

---

### Post by gratefultux on 2006-07-12
I tried FreeBSD before I installed my current ubuntu system.  It's rather different from anything i've used before, and i had some trouble adapting to it.  First off, getting a GUI took a considerable amount of work.  The ports system takes a while to get used to, i prefer the simplicity of apt.  Also, some of the commands used in linux don't exist.  Most notably for me was "dir", which is just something i take for granted after years of using Windows/Dos.  Basically, it's good for server use, but i don't think it's very useful as a desktop.

---

### Post by blitzd on 2006-07-16
I used OpenBSD for 2 or 3 years as a router, only ever rebooted due to power failure and there were 0 patches relevant to my install during that time. The whole system with sshd and sometimes an ftpd/httpd instance ran in less than 24MB of RAM (on a 200MHz CPU if I recall..) I probably could have trimmed it down a bit more, but I only spent about an hour total on configuring it (and I was new to OpenBSD at the time). It ran like a champ until the day the hard drive died - and even then it ran until there was a power failure.. :)

---

### Post by Arisna on 2006-07-16
I ran on FreeBSD on my personal machine for about a month, and on several machines at work and school over the course of about a year.  Once I learned what I was doing, I could do an installation in ten to twenty minutes, and I liked that quick deployment speed.  Also, I concur with previous posts that have praised FreeBSD's thorough documentation.

However, it is not nearly ready for desktop usage.  Command line utilities work great, but you can count on at least one random seg fault every time you start X, regardless of what hardware you are using.  Examples of problems I experienced include crashes when XScreensaver screensavers it didn't like came up, consistent failure of kdeinit to launch Kexi (though it worked well when launched without kdeinit), seg faults when I went to the "Appearance" part of "Configure Kopete," and huge core files dumped in the working directory whenever any of this happened.  Further, audio and video support were less than stellar on my personal machine--audio skipped even with just a few applications running in a light window manager, and DVD playback was extremely sketchy despite hours of troubleshooting.

None of the stuff that failed for me would be needed for a server, but I could not live with it as a desktop.  Ubuntu, and even Gentoo or Slackware, "Just Works" better than FreeBSD for my needs.

---

### Post by WildTangent on 2006-07-16
I run FreeBSD with Gnome on one of my testboxes and I love it. But its very hard to setup. Case in point: I haven't managed to duplicate it since. However, What you can do is use one of the FreeBSD derivatives that have a graphical installer, I'd recommend PC-BSD since it is based on FreeBSD 6.1, and thus has better hardware compatibility. It uses KDE, but its not hard to install Gnome with the ports collection, or if you don't mind using an out of date version, you can install the binary with "pkg_add -r gnome".

-Wild

---

### Post by Rumor on 2006-07-16
PC-BSD's install is great. I especially liked that it gives you the option to not install the bootloader and (on their website) gives the string to put into grub's menu.list manually so you can dual boot with Dapper. It did not recognize my sound card, but identified everything else and was very slick for the brief time I used it.

---

### Post by grte on 2006-07-17
I'm also interested  in giving BSD a try.  My problem is, though, that FreeBSD (The one I've decided to try) only has CD isos available, and I'm out of blank CDs.  I do have DVDs left, though.

Can anyone point me in the direction of a FreeBSD 6.1 DVD iso?

[Edit] Nevermind.  turns out my roomie has got a couple CDs for me.

---

### Post by jonathansizz on 2006-07-30
> the first thing I noticed was the serious lack of software compared to Debian/Ubuntu
> although I don't like bloated distros, found bsd lacking in desktop software

No. There are over 15,000 pieces of software available right now - not far behind .deb based linuxes.


> Basicly, it's a good OS, but hardware support is where Linux was 5 years ago

Slight exaggeration. I assure you that you can run most hardware that you can run on linux.

---

### Post by jonathansizz on 2006-07-30
> However, it is not nearly ready for desktop usage. Command line utilities work great, but you can count on at least one random seg fault every time you start X

I beg to differ. I have had no stability problems with FreeBSD, DesktopBSD or PC-BSD. I have been running FreeBSD on my Desktop for over a year, in which time I have upgraded the OS from 5.4 through 6.0 and now 6.1 - without losing any configuration files or personal stuff, or having to do a clean reinstall.

I use KDE & GNOME and have had things run as expected. Firefox crashes from time to time, but it also does this in Windows and Linux as well. I also have not had any of the problems with sound or video playback that you mentioned having, either.

The main point to remember is that BSD is not Linux. Just as it is unfair for Windows users to complain about Linux simply because it is different from how they are used to doing things, so the same thing applies to Linux users who try out other unixes.

---

### Post by jonathansizz on 2006-07-30
[Frenzy]("http://frenzy.org.ua/eng/")

Frenzy recently went 1.0 and it rocks!

---

### Post by RAV TUX on 2006-07-30
This thread belongs in the "other" distro forum.

I will move it now.

---

### Post by RAV TUX on 2006-07-30
Since the subject matter in this thread will be more appropiate in the "other" Distro thread, I will move it there.

also these 2 threads have been merged:

[http://www.ubuntuforums.org/showthread.php?p=1318006](http://www.ubuntuforums.org/showthread.php?p=1318006)
[http://www.ubuntuforums.org/showthread.php?t=209524](http://www.ubuntuforums.org/showthread.php?t=209524)

---

### Post by silverback011 on 2006-07-30
I guess I am in the minority here.  I have used FreeBSD extensively.  I started with 4.6 and am running 6.1 currently on my desktop.

It is a very good OS.  I have and do use it as a desktop OS as do many other people.  I run KDE 3.5.3 on my desktop along with Fluxbox 1.0 RC2 (if memory serves me correctly).  If you are a person that does not leave the GUI that much you would think I was running Linux.

It is geared toward servers and hardware support is not as extensive as linux.  However, it serves all my needs for a desktop OS.  The only minus is the lack of native Flash.  That does not bother me too much since most web sites abuse Flash anyway.

I prefer it as an OS over linux for many reasons that are not important here.  I use Ubuntu on my laptop because I need a linux distro for work and I don't want to bother with learning the subtle differences between BSD and linux.  Wow, I sound like a BSD snob.

There is a huge amount of software available for BSD.  The current ports system is over 15,000.  It is very stable and secure.  The documentation is very good.  The community is supportive, but they expect you to do some research on your own.

Obviously these are all my opinions.  There are advantages and disadvantages to BSD and Linux.  The good thing is both communities benefit from each other.

If you decide to give it a try I recommend either PC BSD or Desktop BSD.  They are easier to install and get running.  Or if you don't mind taking a little more time you can just download the CD and do a normal basic install and customize the system to your needs.  It takes more time this way.  The advantages are once it is set up you really don't need to reinstall again, and you will learn more.  

Disclaimer:  Poster is biased toward BSD.

---

### Post by tseliot on 2006-07-31
> **jonathansizz said:**
> [Frenzy]("http://frenzy.org.ua/eng/")

Frenzy recently went 1.0 and it rocks!

+ 1

---

### Post by RAV TUX on 2006-08-07
I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.


BSD Talk

---

### Post by RAV TUX on 2006-08-07
I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.

***NetBSD tech Talk***

---

### Post by RAV TUX on 2006-08-07
I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.

***FreeBSD Tech Talk***

---

### Post by RAV TUX on 2006-08-07
I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.

***BSD Tech Talk***

---

### Post by richbarna on 2006-08-08
Ok, we heard you the first time :)
Maybe you need to delete the repeated posts Yozef.

---

### Post by RAV TUX on 2006-08-08
> **richbarna said:**
> Ok, we heard you the first time :)
Maybe you need to delete the repeated posts Yozef.

Done,...my apologies Rich it was a work in progress...:p

---

### Post by richbarna on 2006-08-08
> **yozef said:**
> Done,...my apologies Rich it was a work in progress...:p

That was quick !!! I just thought that with so many new threads, you might have missed this one. I have had a few problems with double-posting lately as well :)

---

### Post by RAV TUX on 2006-08-09
Threads merged:

[http://www.ubuntuforums.org/showthread.php?t=177335](http://www.ubuntuforums.org/showthread.php?t=177335)
[http://www.ubuntuforums.org/showthread.php?t=231318](http://www.ubuntuforums.org/showthread.php?t=231318)
[http://www.ubuntuforums.org/showthread.php?t=30039](http://www.ubuntuforums.org/showthread.php?t=30039)

---

### Post by RAV TUX on 2006-08-09
I'm officially using PC-BSD on my newer computer.

---

### Post by RAV TUX on 2006-08-10
Update: while PC-BSD is nice...I found it not to my liking overall I reinstalled Knoppix on my computer.

---

### Post by baldy1324 on 2006-10-07
yes i have experimented with freebsd and its package managment system in terrible. there are two methods of installing software-
1. ports-cd into directory of app run sudo make install and it compiles dependencies and the app; but updating ports is a nightmare, you have to use cvsup apply patches :mad: 
2. pkg_src is binary and i like it ok; this is what the installer uses when it asks if you want to get additional packages

using two methods is a nightmaree-- but pc-bsd is great with pbi

---

### Post by shining on 2006-10-26
What is that crap?
Freebsd does support both binary packages ready to install with pkg_add, and sources for building them (ports).

From [http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/ports-overview.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/ports-overview.html)
> 
For any given application, the FreeBSD package for that application is a single file which you must download. The package contains pre-compiled copies of all the commands for the application, as well as any configuration files or documentation. A downloaded package file can be manipulated with FreeBSD package management commands, such as pkg_add(1), pkg_delete(1), pkg_info(1), and so on. Installing a new application can be carried out with a single command.
A FreeBSD port for an application is a collection of files designed to automate the process of compiling an application from source code.


However, I had the feeling ports were the preferred method by most fbsd users, so that's what I used, and it worked pretty nice.

---

### Post by stream303 on 2006-11-27
What I like about *BSD is that once you dive into one of them, you can easily switch to another without too much pain.

A *very loose* analogy would be like switching from Debian to Ubuntu or most any other Debian-based distro.

After spending a few years with Free/Net/Open BSD, I found that the cliche of easy-to-use (freebsd), security-only (openbsd), and runs-on-a-toaster (netbsd) were quickly blurred.

You get out of it what you make of it more or less.

For a beginner, your best bet would be to learn an little vi-editing. :)  If you don't like that, ee (easy editor) comes with freebsd, although you can easily download nano, etc for any of them.

Interestingly, OpenBSD kind of frowns on compiling your own kernel for newbies.  YES, you can do it, just don't expect great support for non-standard kernels.  Tweaking is ok via sysctls, but by then you really know why you are doing it in the first place. :)

You can download binary or source packages - your choice.

Just like us, our BSD brethren have a vibrant community - just don't go into it with a Linux mindset - the reverse is also true. :)

---

### Post by loell on 2006-11-27
slightly OT, PCbsd 3.1 beta2 is out , lol the distro logo and the current iso size does coincide with each other , truly it is the "devil's distro" :twisted: :mrgreen:

---

### Post by jan on 2006-11-29
> Now that Debian is going to take on a BSD branch
Did I miss anything??

---

### Post by mips on 2006-11-30
> **jan said:**
> Did I miss anything??

Yes, debian ports to netbsd & freebsd...

[http://www.debian.org/ports/kfreebsd-gnu/](http://www.debian.org/ports/kfreebsd-gnu/)
[http://www.debian.org/ports/netbsd/](http://www.debian.org/ports/netbsd/)

---

