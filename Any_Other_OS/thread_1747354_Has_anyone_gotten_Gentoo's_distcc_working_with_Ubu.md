---
title: "Has anyone gotten Gentoo's distcc working with Ubuntu?"
date: 2011-05-02
forum: Any Other OS
---

### Post by Fraoch on 2011-05-02
I've been playing around with various Linux distros in VirtualBox looking for the lowest memory usage with a working desktop.  The winning combo was Gentoo with Openbox and fbpanel - 18-19 MiB according to conky!

However Gentoo's greatest advantage is also its greatest disadvantage - long compile times!  The target "real" host will be significantly less powerful than my VirtualBox host, although I suppose VirtualBox slows things down considerably.  Still, it took 7 hours to compile Thunar and its dependencies!  I hesitate to think about what the total compile time for the OS the way I need it would take on a slower machine...

distcc to the rescue - maybe?  I had imagined there would be something like this, something that uses the unused computing power of other boxes you have lying around to speed up compile times.

The only other box I have that's up and ready right now is an old Windows XP laptop.  I installed Cygwin which has its own distcc on it.  It didn't work which wasn't surprising given that distcc is running in VirtualBox on an Ubuntu machine, and in Cygwin on another machine running Windows XP.  Just way too many barriers.  Even if it did run, distcc was version 2.18 on Cygwin and 3.1 on Gentoo.  That's a big no-no according to the distcc documentation - distcc will gleefully proceed ahead with distributed compiling, but the combined results may be unpredictable with different versions of distcc.

When I get the real machine up and running, this Ubuntu host will be significantly more powerful than the real machine and could certainly help.  distcc is at version 3.1 in Ubuntu, which is the latest and it should be compatible with Gentoo's distcc 3.1.

Has anyone gotten this to work?

Thanks.

---

### Post by boydrice on 2011-05-03
I haven't used gentoo much but if minimal resources are what you are after look at NetBSD and FreeBSD.  Very little footprint and you have the option of ports or packages.

---

