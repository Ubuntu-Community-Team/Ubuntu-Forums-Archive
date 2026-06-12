---
title: "libstdc++-libc6.1-1.so.2 missing"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by n0idbi0n on 2007-12-04
I'm nearly at the end of my rope here. i've been working with linux for about 3 wks now and the end of this learning curve is nowhere in sight.  Every. single. step. there is a problem.  Can someone please hold my hand like a tiny, helpless child and walk me through this.

I am currently trying to run a java program - but I'm getting the error message:

error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

Ok, i get it.  the file's not there.  it's something to do with c++.  I have other c++ libraries installed, but i guess they're just not good enough.  I followed the related threads where libstdc++-libc6.1-1.so.3 was missing and installed libstdc++2.10-glibc2.2 but no dice.  I also followed another thread and made a "symbolic link" (like a "shortcut" in windows-speak, i presume) to libstdc++.so.6, but I ended up with another error:

Segmentation fault (core dumped)

That sounds bad.  The cores gone.  I don't know if that's related to the library or what.

help me.

---

### Post by spiderbatdad on 2007-12-04
What kind of java program are you trying to run? If we know a little bit more about what you are trying to do, we may be able to better help you.

---

