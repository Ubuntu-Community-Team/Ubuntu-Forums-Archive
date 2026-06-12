---
title: "Create .deb files?"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-10-07
I've seen a few posts on this, but I haven't quite found an answer.  I found this one page on how to set everything up correctly (filename, etc.), but I still don't quite get it.  Lets say I have this script, or file, or few, whichever, that simply need to be moved to a certain directory when you run the package.  Very simple, right!?  Just run the package, it puts it's file(s) in a directory, maybe a few other things, and your done!

How would I do this?

---

### Post by yabbadabbadont on 2007-10-07
Other than using checkinstall which, by default, doesn't provide any dependency information, the only good documentation I've seen on this is here:

[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

Those are the official Debian docs for new package maintainers.  You didn't list what you had already read, so I apologize if you have already seen this.

---

### Post by ryanVickers on 2007-10-07
I'll try the checkinstall if you find me a 64 bit version ;)

---

### Post by yabbadabbadont on 2007-10-07
Setup a 32-bit chroot...  ;)

---

### Post by ryanVickers on 2007-10-07
How would I do that?  I've never been able to run any 32 bit apps except for when automatix installs them :) (rather pathetic actually - they should all just work!)

---

### Post by yabbadabbadont on 2007-10-07
Other than trying to search for you, I can't help with that as I don't have a 64-bit processor.  I just know, from reading the forums a lot, that it can be done for programs for which there are no 64-bit versions.  :D

---

### Post by ryanVickers on 2007-10-07
I've been reading through that page, and it looks like it's mostly about creating a deb file from a source code tarball - I just want to package up some pf my files, and when the package is run, it will move them to a directory and add a menu item maybe...

---

### Post by rsambuca on 2007-10-07
> **ryanVickers said:**
> I'll try the checkinstall if you find me a 64 bit version ;)

There is.  It is in the repos

---

### Post by Frak on 2007-10-07
[http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html)

Though, if you ask us, some of us will be glad to help.

---

### Post by ryanVickers on 2007-10-07
wow, thanks everyone for all the help, but this is just an embarrassment!  :-x I'll see if there's at least one good way of doing such a **simple** task!!! ](*,)

---

