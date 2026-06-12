---
title: "messt up between dpkg and apt-get"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by CareySchug on 2007-02-05
I'm trying to install hercules to emulate an IBM mainframe, to run mainframe linux there.

Previously I installed hercules and c3270, largely without using the various package tools.  I was stuck not being able to enable telnet, which is needed internally for the 3270 emulator to talk to the hercules emulator.

I had to clear the machine to set up a windoze partition, so this time I thought I'd try kubuntu and the "proper" package tools.

I installed hercules with adept.

I couldn't find any 3270 emulator, so I downloaded the .deb package for c3270, and tried to install th at with dpkg -i.

I was told I needed other packages (I don't recall sequence):  a new C compiler and library than came with dapper drake, a newer ssl, 3270-common. The C compiler said it needed tzdata.  I got ssl from apt-get, but the others (I don't think I got as far as 3270-common) by downloading them from the debian site and doing dpkg -i.  However, tzdata said it conflicted with something that provided the same function and could not be installed.

Maybe I should have figured if the function was available, to igore the dependency (I think something I found later implied I could do that), but I tried to start removing all the things with unresolved dependencies.  Unfortunately I shotgunned, and I don't recall what I did, but it included dpkg -r and apt-get remove and "clean" or something like that for each of those, as well as cleaning some stuff out in adept and doing aptitude clean and aptitude autoclean.

However, now I am stuck, I can't get ride of the unresolved depencencies for libc6 and libc6-i686.

How do I clear this all out so I can start over?

---

### Post by deanlinkous on 2007-02-05
I would start with **apt-get -f install** and post back any errors it still throws...

---

