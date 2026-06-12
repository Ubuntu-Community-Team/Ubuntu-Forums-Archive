---
title: "Downgrading"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Stringsy on 2007-08-24
I searched the forums, but couldn't find something that really helped.
This is what happened. (this is Debian btw)

I edited my sources.list to include testing.
I then did some pinning, making testing lower than stable.
I then ran aptitude to get **rtorrent**, modifying it in order to get the package/dependencies from testing.
What happened next was a very very very very very very very long installation and upgrade by the looks of things. It would seem that I inadvertently updated a **** load of packages when I did this.

I've since been told that Etch backports are the way to go, far less dodgy than mixing versions. So I need to remove rtorrent and downgrade all the packages that accidentally got upgraded to their versions from testing.

Unfortunately, I can't seem to find a decent guide/tutorial on how to properly complete this. I have a gist of what to do... but nothing explicit. Here's what I think I have to do.

**1.** Comment out everything but "stable" release in the sources.list
**2.** I then need to go to preferences and use this:

 Package: *
Pin: release a=stable
Pin-Priority: 1001

And it's here I get stuck.

Would I just use aptitude upgrade?

Should I aptitude purge rtorrent first, before I do any downgrading?

I just don't know what to do after step 2 in context with aptitude :(

---

### Post by wolfen69 on 2007-08-24
instead of spending MANY hours trying to fix this, why not re-install in 20min.? i'll never understand why some people will spend days working on a problem(not you) instead of re-installing. if everything is backed up like it should be, it should be no big deal. just my opinion.

---

### Post by Stringsy on 2007-08-26
Well yeh....

But it's hardly good practice to just re-install whenever something goes wrong. I'd rather try and tackle these kinds of problems properly.

Anyone else know how I could fix this problem?

---

### Post by phenest on 2007-08-26
> **wolfen69 said:**
> instead of spending MANY hours trying to fix this, why not re-install in 20min.? i'll never understand why some people will spend days working on a problem(not you) instead of re-installing. if everything is backed up like it should be, it should be no big deal. just my opinion.

Because the solution maybe faster than re-installing, and can be passed on to others with the same question.

---

### Post by Stringsy on 2007-08-26
Anyone?

---

