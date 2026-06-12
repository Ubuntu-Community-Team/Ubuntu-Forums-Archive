---
title: "gettext installed yet not found"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by 0o0 on 2008-01-17
i was trying to install a few things here and there it said i need glib 2.0 so i downloaded the glib and try to do ./configure and it gives me error gettext not found so i installed that and its still not letting me install glib it says gettext not found

checking for msgfmt... no
configure: error:
*** You must have either have gettext support in your C library, or use the
*** GNU gettext library. ([http://www.gnu.org/software/gettext/gettext.html](http://www.gnu.org/software/gettext/gettext.html)


thanx for the help

---

### Post by SOULRiDER on 2008-01-17
What exactly are you trying to install? =/
AFAIK glib should already be in your system, its in the repositoreies anyways, so you can just install it with
```
sudo aptitude install libglib2.0-0
```

---

### Post by 0o0 on 2008-01-17
i just needed glib 2.0 to install amsn and beryl and etc i did what u said but its still giving me error that glib 2.0 is not found

---

### Post by SOULRiDER on 2008-01-17
#1 Beryl is old, compiz fusion is what appeared after Veryl and Compiz merged back. CF is already installe din gutsy, its what provides desktop effects there.

#2 For aMSN check out this thread [http://ubuntuforums.org/showthread.php?t=297676](http://ubuntuforums.org/showthread.php?t=297676)

---

### Post by Hospadar on 2008-01-17
you probably need "libglib2.0-dev" for your build error.  but as above, you should use compiz, it comes standard in ubuntu and is better than compiz.  Go to System->Preferences->Appearance->Visual Effects and turn them to "normal" or "extra"

If you want full control of compiz as reminiscent of the old beryl settings manager, install compizconfig-settings-manager from synaptic and get to it from System->Preferences->Advanced Desktop Effects Settings

Note also that in general, when you are building stuff, and it has some library as a dependency, you'll need to get the lib<whatever>-dev package, it has the C/C++ headers needed to compile with that library.

---

