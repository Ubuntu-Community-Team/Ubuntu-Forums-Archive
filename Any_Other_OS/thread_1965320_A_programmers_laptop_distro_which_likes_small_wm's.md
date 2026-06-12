---
title: "A programmers laptop distro which likes small wm's."
date: 2012-04-25
forum: Any Other OS
---

### Post by xmorg on 2012-04-25
Can you help me find a distro that works for me?

I left Ubuntu after an "update" threw the openGL files out of /usr/include and /usr/lib into some obscure directory in the include and lib trees.  After I finally found the files, and after having to modify my makefile which worked perfectly days before, it never would link my programs, and got lots of undefined symbols. This is a fundamental problem I have with linux distros is 1, moving things around constantly, and 2, lacking any sense of compatibility or creating a "sane" build environment.  I mean sane as in sanity not ./configure.

I have a similar issue with fedora 16.  The gcc/g++ verion is so "new" that the majority of things I have tried to compile with it get "not declared in this scope" errors. (linley's dungeon crawl and zsnes, pillars of the linux gaming scene!), C apps are ok but C++ apps dont compile

So here is what I am looking for.
* ITs netbook, so laptop friendly, USB disk installer because it has no cdrom.
* A very General Distro that doesn't rely heavily on Unity/Gnome/KDE. I like to take the pieces from these I want, to create my frankenstin OS monster.
* I like to customize my system, try new things and dabble in programming. So:
 
1) Please at least include GCC and headers! lol. ( a developer centered distro)  Also a majority of bleeding edge open source software is distributed in source form, and the only way to install is to compile it. /configure, make, make install.  Not everything is expected to work but having a standard /usr/include(see 3) helps!

2) "standard" GNU tools would be nice.  Its a pain to go package hunting for tools that have traditionally been in linux. (ex: gcc, grep, gmake, autoconf, etc) and since in fedora's case this "optional" tool is may be a requirement in thousands of packages, a search by name would be an very long query.  Ubuntu has better package management.

3) more "standardized" file locations.  I dont think moving foo.conf from /etc to /etc/foo/allfoos/fooorg/newxmlfoo/xml is an "improvement".  This is a BIG issue for me, and one of the reasons I have used FreeBSD instead of linux for years.  Every upgrade, i feel like a blind man who got his bedroom rearranged.
 
* Power management and Wireless that are NOT integrated into its flagship desktop, ubuntu and fedora have this issue.  If I login to pekwm, I cant connect to the internet!  I also cant put it into hibernate without making a script.

* Package management that is NOT integrated into its flagship desktop. Ex: fedora 16, attempting to install a flash update RPM from hackedbox, would not let me verify with a password and just said, you're not authorized.  It was waiting for Gnome to ask for a password but there WAS NO GNOME!


More pluses

* Not even having a flagship desktop!  I change window managers like underwear ( i like to experiment)

* Compatibility.  I have ranted about this before, but you buy a Humble Bundle game, and cant seem to find a linux distro it works on, usually because the glibc is too new or too old etc.  This is hard since linux is always changing so thats why this i a plus.

* Small but not minimalist. I like distros that are CD sized, my largest USB drive is 4GB so unfortunately i wont try slackware because it so large.

* Why split up runtime and development packages?  Ex: the sourcecode for SDL is 3.7 megs.  But I need to go package huting for SDL-devel/GL-devel, and everythingelse-devel in a lot of distros???  Does it really hurt to put tiny header files in /include?

---

### Post by lykwydchykyn on 2012-04-25
I can't speak for all those requirements, but I would guess Arch or Slackware would be good; they both have a reputation for keeping things simple and not over-tinkering with upstream.  Also very compile-friendly.

Good luck!

---

### Post by boydrice on 2012-04-26
To my ears what you are describing sounds like Slackware would be the answer.  A 4gb usb stick is just fine for a usb install.  Just have a look at the usb readme [http://ftp.nluug.nl/os/Linux/distr/slackware/slackware-13.37/usb-and-pxe-installers/README_USB.TXT]("http://ftp.nluug.nl/os/Linux/distr/slackware/slackware-13.37/usb-and-pxe-installers/README_USB.TXT")

---

### Post by ratcheer on 2012-04-26
**Arch or ArchBang. Gentoo or Sabayon. **The first of each pair is a general distro that you have to work to configure. Of course, this comes out exactly the way you want it. The second of each pair is based on the first, but tries to give an "out-of-the-box" experience. ArchBang is probably closer to Arch than Sabayon is to Gentoo. But Sabayon is quite a neat distro. I give thumbs up to all four.

Tim

---

### Post by Herpythebrony on 2012-04-27
May I suggest Crunchbang?

---

### Post by codingman on 2012-04-27
Slackware or Debian Squeeze.

---

