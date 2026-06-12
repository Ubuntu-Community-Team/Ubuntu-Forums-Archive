---
title: "x64 vs. x86"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by naoise on 2007-02-06
How do you know which version was installed? or does it just 'know' and automatically do so. I need to know in order to be able to write to sata drive

thanks

---

### Post by BarfBag on 2007-02-06
Do you mean 32 bit vs. 64 bit?  There's two versions of Ubuntu.  One of them is 32 bit, the other is 64 bit.  If you have a 64 bit processor (AMD Athlon 64, for example), you'll get better performance out of the 64 bit version.  The only problem is the immaturity of 64 bit packages.  You'll have to compile a lot of things yourself.  The 32 bit version might be slightly slower, but for now - I recommend it.

To answer your question - no.  Ubuntu will not automatically install a 32 or 64 bit version.  You have to decide which one you want, and install it yourself.

---

### Post by naoise on 2007-02-06
at what point? I'm installed and facing other issues.I grabbed the package from the .com site, but i didn't see different packages. It just gives a path to server, no version options.

---

### Post by radio_flyer on 2007-03-21
On the [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) page there is the question "What type of computer do you have?" Choose "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)" for 32 bit and "64bit AMD and Intel computers" for 64 bit.

a) To check on your iso cdrom install disk, mount it and view the README.diskdefines in the root directory of the cdrom. The ARCH line will show which version it is (it's #define ARCH i386 on my system).

b) For a running system, try this (don't type the quotes):
1) Open a terminal window (applications-->accessories-->terminal) and type 'python"
2) At the ">>>" prompt, type "import platform"
3) At the ">>>" prompt, type "platform.architecture()"
4) The response will be something like "('32bit', '')"
5) Type CTRL-D to exit

I don't have a 64-bit system system myself but I believe the above would work. Perhaps someone with a 64-bit system could post their results for a) and b) above?

---

