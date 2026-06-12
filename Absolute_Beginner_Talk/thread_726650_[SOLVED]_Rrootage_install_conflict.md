---
title: "[SOLVED] Rrootage install conflict"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by alistairw on 2008-03-16
Hey, new user here - I seem to be having quite a few libsdl issues though. For example, I'm currently trying to install Rrootage (Kenta Cho's games were favourites back on Windows), but I keep running into this little monkey:

>  Depends: libsdl-mixer1.2 (>=1.2.6) but it is not installable

It even happens in terminal, giving me this message:

>  Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  rrootage: Depends: libsdl-mixer1.2 (>= 1.2.6) but it is not installable
E: Broken packages

And when I try to install libsdl-mixer1.2 on its own, I get this:

>  Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libsdl-mixer1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libsdl-mixer1.2 has no installation candidate

I'm assuming there's a really simple thing that I'm doing wrong. I'm using 7.10, by the way.

Ta.

---

### Post by Xiong Chiamiov on 2008-03-17
That is odd.  I installed rrootage just fine, and libsld-mixer1.2 shows up just fine in aptitude.  You might want to check which repositories are installed, or download the package [here]("http://packages.ubuntu.com/gutsy/libsdl-mixer1.2").

---

### Post by alistairw on 2008-03-17
Thanks - that's all cool. I managed to work out where to download packages from, and I'm building the rest of the Kenta Cho collection as we speak. Now I just need a Linux version of Warning Forever, and I'll be happy!

---

