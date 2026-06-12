---
title: "How to use gnome pitch"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by kikidai on 2007-06-25
There is a bug for using KDE programs in Gnome.  The app blanks very often in all the workspace. The discussion is:

[http://bugzilla.gnome.org/show_bug.cgi?id=400167](http://bugzilla.gnome.org/show_bug.cgi?id=400167)

A pitch is given. 

[http://bugzilla.gnome.org/attachment.cgi?id=90201](http://bugzilla.gnome.org/attachment.cgi?id=90201)

But, how can I use this pitch?

Thanks a lot.

---

### Post by jrib on 2007-06-27
You mean "patch" I guess?

You need to download the source for the package the patch applies to, apply the patch (see 'man patch', it's pretty readable; or google for a tutorial), then rebuild the  package and install it.  See 
[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html) .

If you want to learn and help out, great, but if you're a new user who's not comfortable yet, I wouldn't recommend doing this.

---

