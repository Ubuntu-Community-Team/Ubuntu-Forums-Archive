---
title: "52 Updates???"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by Irony on 2005-09-13
I've just switched on my computer today and noticed 52 updates mainly of lib packages - I was fully updated yesterday. Normally I just get 1 or 2 updates.

Is this amount of packages normal for my sources list - I'm a bit wary of updates 'cos I keep reading of them breaking ubuntu;

[PHP]deb-src http://gb.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe[/PHP]

---

### Post by mlomker on 2005-09-13
It looks like your repositories are only the official ones.  It should be okay.

---

### Post by Irony on 2005-09-13
Thanks for quick reply.

It occurs to me that I updated the kernel (linux-image-2.6.10-5-386, new version: 2.6.10-34.4) a few days ago, so perhaps it is related to that?

---

### Post by Stormy Eyes on 2005-09-13
[QUOTE=Irony]Thanks for quick reply.

It occurs to me that I updated the kernel (linux-image-2.6.10-5-386, new version: 2.6.10-34.4) a few days ago, so perhaps it is related to that?[/QUOTE]

Most of the updates are probably security updates relating to the X Window System (your graphical display subsystem).

---

### Post by Irony on 2005-09-13
Yes they are mostly X windows related.

Normally I just note what the update is, so if it messes things up I can un-update it - I suppose in this case as there are so many I can note the *New Version 6.8.2-10.1* number and relate it to that.

---

### Post by wmcbrine on 2005-09-13
I got 117 today, totalling 124 megs.

---

### Post by Nequeo on 2005-09-13
So far as I can tell, we're feeling the backlash from the modulization of X server

Previously, all of Xorg was one great big package, full of useless junk and drivers that most people wouldn't need. Xorg has now has been broken up into LOTS of smaller packages, which is a Good Thing. This 'modularized' version of X has been in Breezy repositories for quite a while.

We're seeing it in Hoary too, now, either because that's how they're distributing the security updates now, or because they're trying to pave the way for a more seemless upgrade to Breezy.

---

### Post by skoal on 2005-09-13
52 updates?  Sounds too much like that card game "52 pickup".  I think I'll pass...

\\//_

---

### Post by Nequeo on 2005-09-13
[QUOTE=skoal]52 updates?  Sounds too much like that card game "52 pickup".  I think I'll pass...

\\//_[/QUOTE]
 I love the smell of updates in the morning.

Smells like... progress.

---

