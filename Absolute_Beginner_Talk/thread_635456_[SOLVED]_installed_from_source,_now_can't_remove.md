---
title: "[SOLVED] installed from source, now can't remove"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by iris-n on 2007-12-08
In a attempt to get some software working the hard way, I donlowaded glib-2.12.0 from source and managed to install it. But my system didn't seem to like it, listed a conflict with libglib2.0-0, that I ignored. Now my system wont start the GUI. I guess removing the new glib would solve the conflict, but how I do it?
Thanks ^^

---

### Post by rsambuca on 2007-12-08
In the folder that was created when you extracted the tarball there should either be an uninstall file or instructions in the readme.  If you didn't keep the folder, I have no idea.

---

### Post by jordanmthomas on 2007-12-08
With a lot of software, you can uninstall it with
```
make uninstall
```
This usually requires the software to be built first, so you may have to download and recompile it before you can do it.

---

### Post by iris-n on 2007-12-08
I have indeed kept the original folder, not so foolish a noob. Read through the readmes, quite hastily I admit, but found only information on installing.
Nevertheless I tried the make uninstall one, and as soon as the uninstall completed, my X popped open =)
Thanks a lot, and sorry for the sheer ignorancy.

---

### Post by logos34 on 2007-12-08
consider using auto-apt and checkinstall in the future

---

### Post by jordanmthomas on 2007-12-08
> **iris-n said:**
> as soon as the uninstall completed, my X popped open =)


That seems suprisingly easy.  I would have expected a bunch of problems after you uninstalled it too.  :)

---

### Post by iris-n on 2007-12-08
Well, that's a sane advice.
Only installed from source because apt-get didn't have the package I wanted. For a good reason now I know.
But what is auto-apt and checkinstall?

Me too, was my last shot before I ran the live CD and reinstalled gutsy from scratch.
I started the terminal at the boot stage, whilst X was frozen on loading.

Now I just don't understand the conflict, after all the source I got was from gtk site, hoped it would replace/upgrade my existing one.

---

