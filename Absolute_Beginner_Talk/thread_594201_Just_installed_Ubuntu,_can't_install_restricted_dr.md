---
title: "Just installed Ubuntu, can't install restricted drivers"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-10-27
I get the error message "the software source for the package isn't enabled."  I know why, but I don't know how to fix it.  When I was installing Ubuntu, it said something to the effect of "cannot find security updates.  Look into this later.  Sources commented out."  This happened because I'm on a university network and you have to log in to it before you can be on the internet, and you can only log in it through a browser.  

Now, how do I uncomment out the source?  I know there is a file to edit, but I can't remember which file it is.  Can someone point me the right direction?

---

### Post by DezSP on 2007-10-27
There's a GUI, last I looked. System -> Administration -> Software sources, add the 'restricted' repository, then run apt-get update or equivalent.

[This is, incidentally, a known issue of restricted-manager, which should really be clever enough to work out if restricted is actually enabled or not.]

---

### Post by skompier on 2007-10-27
Sounds like you need to enable the restricted driver source. Go to System>Administration>Software Sources and check that Proprietary Drivers is checked.

---

