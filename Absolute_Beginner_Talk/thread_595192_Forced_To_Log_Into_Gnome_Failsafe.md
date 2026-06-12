---
title: "Forced To Log Into Gnome Failsafe"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Mijikai on 2007-10-28
I was attempting to install Compiz Fusion on my newly upgraded Gutsy.  I was following the advice of a few How To's ([http://ubuntuforums.org/showpost.php?p=3547899&postcount=8](http://ubuntuforums.org/showpost.php?p=3547899&postcount=8) and [http://ubuntuforums.org/showpost.php?p=2938823&postcount=1](http://ubuntuforums.org/showpost.php?p=2938823&postcount=1)).  After I finished the first, the login screen appeared and I tried to startup into Gnome.  After entering my username and password, it looked like it was going to log in, but then flashed to a black recovery-mode looking screen (I believe saying it was running my startups at the bottom) before returning me to the login screen.  It does this for all options except failsafe Gnome and failsafe Terminal.  Any help with this would be GREATLY appreciated.

---

### Post by oldos2er on 2007-10-28
Compiz is installed by default in Gutsy, as long as your hardware supports it. Maybe try uninstalling what you've installed...?

---

### Post by Mijikai on 2007-10-28
Will try to undo what I did in the How To's.  I will post a reply ASAP.

---

### Post by Mijikai on 2007-10-28
Ok, so I did steps 1-4 in this How To:  [http://ubuntuforums.org/showpost.php?p=3547899&postcount=8](http://ubuntuforums.org/showpost.php?p=3547899&postcount=8).

I was able to boot up into gnome, but then I opened a terminal and typed fglrxinfo.  I got the following message:
```
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

I take this to mean that I don't have the ATI driver(s) installed properly.  I'll look for a good How To thread on how to properly do that...unless someone posts one here before I find one :).

---

