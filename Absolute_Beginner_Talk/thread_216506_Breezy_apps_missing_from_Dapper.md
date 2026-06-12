---
title: "Breezy apps missing from Dapper"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by brn on 2006-07-15
I just installed Dapper and tried to apt-get a couple of packages that were present in Breezy.  No longer there.  I downloaded a .deb binary from one of the sources but it needed yet another debian lib file which I then retrieved but it was likewise refused installation.  What to do?  Can I mount the original (Breezy) CD and apt-get from there?  (I find nothing about this in the apt-get man page) or must I install gcc and g++ and try to do battle with some very convoluted makefiles.  Another choice, dump Dapper and reinstall Breezy.

Thanks!

---

### Post by Kurt` on 2006-07-15
Have you edited /etc/apt/sources.list to include ALL of the possible repositories?

It could be that the programs you are referring to are in one of the other repositories (that are commented out by default).

Remember to apt-get update after editing sources.list!

---

### Post by mostwanted on 2006-07-15
It would be very helpful if you also wrote what packages you are trying to install :)

---

### Post by brn on 2006-07-15
Thanks Kurt, I uncommented all the debian lists and that got me a long way.  The package I most want at the moment is gforth which I'm certain was on the Breezy list but is gone now.  Tangling with 'C' is something I have carefully avoided for more than 30 years so I know I didn't install it that way for Breezy. ;)

---

