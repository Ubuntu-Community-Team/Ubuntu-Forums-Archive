---
title: "Installing Limewire?"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by Sonic5688 on 2005-12-01
I downloaded Limewire and don't know how to install it. The only things I've installed so far were through the Synaptic Package Manager. Thanks!

---

### Post by TeeAhr1 on 2005-12-01
Okay, what's the name of the file you've got?  Does it end in something like .tar or .tar.bz2?

---

### Post by Sonic5688 on 2005-12-01
It was an RPM file. i extracted it to my desktop and got a folder called usr, and inside it were 3 other folders called bin, lib, and share.

---

### Post by aysiu on 2005-12-01
[https://wiki.ubuntu.com/P2PHowTo#head-7fb2803e9171c3a6b582e29c5bf1a7b907b4044b](https://wiki.ubuntu.com/P2PHowTo#head-7fb2803e9171c3a6b582e29c5bf1a7b907b4044b)

---

### Post by TeeAhr1 on 2005-12-01
An RPM file?  Okay.  Backtracking a little bit for clarity's sake, if you already know this stuff, forgive me.

RPM = Red Hat Package Manager.  Red Hat's version of ".deb" which stands for Debian Package Manager.  The only way to get an RPM package to work correctly is to have the Alien utility installed.

Do you have Alien installed?  If yes, I can't help you, I don't know squat about it.  If no, you downloaded an incompatible file for your system, and we need to either find one that works (.deb or .tar) or install Alien.

---

### Post by Sonic5688 on 2005-12-01
Oh, ok. thank you! does this mean all my programs that i want to install must be a .deb file?

---

### Post by TeeAhr1 on 2005-12-01
No, not at all.

.deb is something that you can install using synaptic or, from the command line, apt-get (same thing, different interfaces).  In short, when you were using Synaptic, it was downloading and unpacking .deb files.  [Here]("http://www.newsforge.com/article.pl?sid=04/12/02/1710208") is an excellent primer on .deb and apt-get.

This does not mean that's all that is available to you.  You can manually unpack .tar files (if you're a windows native, think of .deb like an installer program, and .tar as a zip file - not an exact analogy, but kind of close).  There are lots of options, but I'm just barely ahead of you on the learning curve, and I haven't dove into things like compiling source code.

Anyway, we're getting ahead of ourselves here.  Go back where you found the RPM file and see if there are other options, and post back with your findings.

---

