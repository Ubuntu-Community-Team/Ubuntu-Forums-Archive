---
title: "Why we do things the way we do them (compiling from source, distribution packages)"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Andorien on 2007-07-27
As I dive more into Linux, I've begun to wonder something.

As I understand it (and please correct me if I'm wrong), the current system of downloading pre-compiled binaries for extra components or grabbing the source code and making it yourself is derived from the fact that Linux is a little loosely defined, and there's no real way to guarantee a "Linux" program will run on your distribution unless it's been compiled specifically for you.  It would seem to me that this is a bit of a barrier to commercial offerings, as most companies are loath to release their source code, and they can't give a binary for every type of linux.

In light of this, what's stopping the development of something akin to a "Linux Abstraction Layer"?  Basically, this API would be to Linux what Direct3D/OpenGL are to video hardware.  It sets up certain standards, forms an API, and it's the responsibility of the distribution to implement it (just like video card manufacturers must implement Direct3D/OpenGL).  In this way, you could grab a universal "Linux" binary that's written using this API, and as long as your distro fully implements it, it's pretty much guaranteed to work.

So am I completely off base and should shut my mouth?

---

### Post by Rocket2DMn on 2007-07-27
One reason to provide source code to compile is so that people can modify the code to their liking.  They can develop off of it (under the GPL), or just tweak to their preferences.  Hence Free and Open Source Software (FOSS).  Also, so much is changing constantly, the code sometimes needs to be recompiled to correctly link to shared libraries and other dependencies.
The ability to build the program yourself can also allow the compiler to tweak the program to meet your computer's processor/board architecture and run better.  Linux has much better support for different architectures that other systems like windows.  It's just a lot more dynamic.

---

### Post by DC@DR on 2007-07-27
Actually I wonder the same thing, and I think it's what Linux Standard Base ([http://www.linux-foundation.org/en/LSB](http://www.linux-foundation.org/en/LSB)) are aiming for. It would ease a lot for distributing and maintaining packages between distros if there's a standard that everyone follows :-)

---

### Post by OoooMatron on 2007-07-27
I run a few programs that are already compiled and executable, so what makes this such a large problem? That's not a rhetorical question btw because I have pondered on the same question. Why do we need to compile distro specifically when there are a bunch of closed source applications that work across the board?

Second Life works without being compiled. As do the MySQL tools and Nero Linux for example. Then there are the obvious Java apps like Azureus and Zend Developer which run so good under linux compared to windows.

But truly, I don't want to see Linux become windows and suddenly the only thing you can get for Linux are 3rd party closed source applications. Practically everything I run on Linux is open source and it feels really good not to be dirty and have a load of stolen applications running on my machine.

---

### Post by Jeek Elemental on 2007-07-27
I agree its abit confusing, what youre asking for is basically the Synaptic/aptitude package manager tho?

Im still a gnub \\:D/ so apply salt.

gnu/linux can be run on any number of processors, however precompiled binaries can only run on the processor it was compiled for. So if you distribute something as source, the benefit is that one package fits all.
Also when compiling specifically for your processor, you get to use all of its capabilities.

the aptitude system works great but theres some lag between releases and a finished package, and for performance critical stuff youre unlikely to get the best possible (ie 386 binaries running on athlon x2s).

The problems arise more from the dependencies than anything else I think, and while you can use wrappers of all sorts to limit this it gets messy and unpredictable.

A compromise, somewhere between source and precompiled is mono and .net, where applications basically get compiled on the fly, as I understand it.

---

### Post by Mornedhel on 2007-07-27
Andorien, are you talking about a programming API of the kind Windows has in the MFC and successors ? In that case, there already are such things : GNOME applications, for instance, follow the GNOME guidelines and use a common toolkit (GTK+). KDE ones do the same.

If you're talking lower-level, there are commonly available librairies for that. Linux applications are much more modular ; for instance, if I want to develop a music player in Perl, I can use the corresponding mpd and GTK+ Perl modules which are available for any Linux (OK, so it's a few levels higher than librairies, but you get the idea), and presto, I have an mpd client that plays MP3, Vorbis and FLAC. And if you're talking even lower-level, the kernel is your API.

Precompiled binaries, however, work great on any platform (32b/64b conflicts set aside, and I'm not talking about specific architectures - Sun stations, etc.). For instance, you can install UT2004 from the original CDs, as they have kindly provided an installation shell script. I can't see the source ; I don't compile them myself ; yet it works under any flavour of i386 Linux (and probably amd64 based ones). You'll notice that many other companies do the same - Sun's JVM for instance can be obtained as a .deb, a .rpm (Red Hat's packages) or precompiled unpackaged binaries (it is only near the end of 2006 that Sun released their sources as GPL).

---

