---
title: "Installing Software"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by the gnome on 2006-12-01
There are lots of options to get software installed on Ubuntu (i.e. apt-get/aptitude/synaptec/compile).  I'm alsa a newb admin of a remote Debian box.

I am of the understanding that in Debian you never want to get away from the apt-get packages, or mix versions (i.e. do not grab a testing version of apache if you're running a stable version of the OS).

After making plenty of mistakes on the Deb box, I'm trying not to do the same in my development machine.

The problem lies in the fact that I'm setting up a box for Ruby on Rails development.  Seeing as that tech is so bleeding edge, new versions of my development tools come faster than packagers can package and test them.  I'm therefore very tempted to get out of the package scheme on a regular basis.

After a long winded preamble I suppose my question is this:  How bad is it to compile new versions of software I need (say Ruby, or Apache) rather than going through one of the package managers?

---

### Post by Bachstelze on 2006-12-01
Not bad *at all* ! Packages just make your software easier to manage but installing stuff from source can do no harm.

---

### Post by the gnome on 2006-12-01
Ok thanks!

Right now I'm using ubuntu as a dev box, but if I can get comfortable enough, I'm thinking of switching over completely.  Is there a site that lists and reviews Linux software?

There's download.com for win/mac software, is there anything similar for Linux?  I'd love to browse what's available and check out some screenies.

I ended up downloading just random things from synaptec and liking some, but I always wondered what else was available.

---

### Post by lumpki on 2006-12-01
Well, there's [http://freshmeat.net/](http://freshmeat.net/). I'm always discovering new and cool programs, there are boatloads. When I'm itching for a new game, I check [http://www.happypenguin.org/](http://www.happypenguin.org/).

Sometimes I find stuff when I need to do a certain task and start searching. And often I just stumble across neat new things to try out, browsing linux.com or newsforge.com.

---

### Post by az on 2006-12-01
> **the gnome said:**
>  How bad is it to compile new versions of software I need (say Ruby, or Apache) rather than going through one of the package managers?

You can do that if you like, but forget about using the repositories to upgrade from one release to the next without a lot of headaches.

Usually, for a server, you keep the infrastructure stable by getting things from the repos and run your web application from source.  But if you really need a bleeding-edge version of rails to work with, perhaps try the developmental version of Ubuntu?

---

### Post by CatKiller on 2006-12-01
> **the gnome said:**
> How bad is it to compile new versions of software I need (say Ruby, or Apache) rather than going through one of the package managers?

Actually, if you install the **checkinstall** package, it becomes a false dichotomy. You can compile it and still have it entered into your package management system for easy upgrade/uninstall.

---

