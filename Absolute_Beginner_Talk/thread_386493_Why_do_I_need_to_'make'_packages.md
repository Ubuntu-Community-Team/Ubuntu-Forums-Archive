---
title: "Why do I need to 'make' packages?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Inbo on 2007-03-17
Sorry if this is an obvious question and I am still very newb, but I've been using Windows since it came out on 3.1 and I don't understand why configuring and making packages is necessary. Why can't they just be installed automatically like debian packages?

---

### Post by aysiu on 2007-03-17
Well, a Debian (.deb) package has to be available. If one is not available, there may be an .rpm you can *alien* to a .deb. If not, then you will have to compile from source (that's the ./configure make make install business).

More details here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Inbo on 2007-03-18
thanks

well that didn't really answer my question, but I realized it is a dumb question anyway

---

### Post by AtrejuT on 2007-03-18
basically it means the following:
.deb-packages contain executable files (and libraries, and artwork etc.) (like the things you usually get in windows) - so to install it basically all you need to do is put all these files in the right place. This is what happens if you install a .deb-package.
For some software however there are no precompiled .deb-packages, so all you can get is the source code of the programme. So in order to install it you first need to compile it, that is to make executable files from the source (make) and then put these files in the right place (make install).
make is just the command that compiles the source for you.

atreju

---

### Post by freebird54 on 2007-03-18
The only dumb questions are those that are not asked.

Have you checked out the Add/Remove programs entry under Applications?  Or the Synaptic package manager under System->Admin ?  There are thousands of packages ready to be auto-installed there.... (Debian style)

---

### Post by 3rdalbum on 2007-03-18
I believe I have the answer you're looking for.

You're asking why there aren't just Debian packages of everything, right? Well, there are two reasons:

1. Not all distributions use Debian packaging - most use RPM packages.
2. A Debian package contains only prebuilt binaries for a single architecture, which would make the thing useless for people on 64-bit, PowerPC, Itanium, Sparc etc. You can't run code compiled for x86 on a Sparc, for instance.
3. The same is true for a "binary installer" like you're used to on Windows (e.g. setup.exe). Windows only runs on one architecture, so binary installers aren't much of a problem (except for the emergence of 64-bit PCs). But binary installers have another problem - they cannot tie into package management systems. Linux users generally like to have one place to go for all their installing and uninstalling.

The "lowest common denominator" is source code. Actually, I'm in the process of drafting a package management system that uses source code as its base, so you'd be able to download a single file that will easily install on all distributions AND tie into the native package manager to download dependencies and whatnot. Should be good.

---

### Post by kinematic on 2007-03-18
> **AtrejuT said:**
> 
in order to install it you first need to compile it, that is to make executable files from the source (make) and then put these files in the right place (make install).
make is just the command that compiles the source for you.

atreju

actually...../.configure compiles the source code into binary form wich your computer can read,make makes the executeables and make install installs it.

---

