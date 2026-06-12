---
title: "Install .deb file woes"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-03-18
Hi,
I've encountered this issue with two or three applications in .deb archive format. Let's use, for example, yamysqlfront_0.6_i386.deb which I downloaded from the Yet Another MySQL Front website. I chose to open it with gdebi-gtk, which then tries to install it, then gives me an error:
Error: Dependency is not satisfiable
libglademm-2.4-1c2

So, I opened the Synaptic Package Manager in hopes of resolving this issue. I find and install libglademm-2.4-1c2a, as libglademm-2.4-1c2 isn't an option, even when I tick all the boxes in the Repositories dialogue. When I try to install then, it still gives me the same error.

I've had this issue with a few .deb files... I'm convinced I must be missing a step.
Anyone have any ideas?

Cheers,
Robyn

---

### Post by lloyd_b on 2007-03-18
I've had a similar situation with a different package.  The problem is that the package builders are a bit too specific as to the version (hence that "c2a" business).  Most likely, that package will work just fine with the "...c2a" library, but because of the naming issue package manager programs will never realize it.

What you can do - open a terminal window.  "cd" to the directory that the .deb file is in (if it's not in your home directory).  Then:
```
sudo dpkg -i --force-depends yamysqlfront_0.6_i386.deb
```
This will install the package, but ignore any dependency errors that would otherwise prevent the installation.  Then try out the program and see if it works.

Don't be too surprised if the program doesn't work as expected.  There may have been a valid reason that the package builder specified "c2" and not "c2a".  But most likely there is no such reason, and the package will work just fine with that library.  Unless there's a real danger of that program damaging important files, I'd suggest just going ahead and trying it.

(And if there's a real danger of damaging important files, I'd recommend staying away from any project that's only at rev 0.6!).

Lloyd B.

---

### Post by Robynsveil on 2007-03-18
Fair enough, Lloyd, and thanks for that! All in all I've found Ubuntu a brilliant piece of work - I *am* delighted with it. I figure once I've got my head around some of these concepts - the next I want to tackle is 'make' - I'll never boot to XP anymore.

Cheers mate,
Robyn

---

