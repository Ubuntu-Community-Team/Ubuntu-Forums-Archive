---
title: "Trouble installing libavutil1d and updating libc6-dev on Dapper 6.06/AMD64"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by isync on 2007-10-01
I am trying to install libavutil1d_0.cvs20070307-5ubuntu4+medibuntu1_amd64.deb from the medibuntu repository.

I open it with right-click-"instalkl with GDebi-Packet-Installer" and after the startup GDebi says: "Error: Dependency is not satisfiable: libc6" althoug I have all libc6 packages installed libc6 and libc6-dev in version 2.3.6.0ubuntu-20.5 ...

Details are:
libavutil1d depends on libc6 (>= 2.6-1); but: version of libc6 installed is 2.3.6-0ubuntu20.5.

Is this related to this bug: [https://bugs.launchpad.net/ubuntu/+bug/138602](https://bugs.launchpad.net/ubuntu/+bug/138602) ??

**Update:**
I found out Dapper uses version 2.3 of libc6
Edgy 2.4, Feisty 2.5 etc.
Is it possible to have 2.6+ on Dapper (to be able to install the latest libavutil) Or can I force to install although I run an older libc6??




This thread is related to [http://ubuntuforums.org/showthread.php?p=3456320](http://ubuntuforums.org/showthread.php?p=3456320)

---

### Post by isync on 2007-10-01
> **SD-Plissken said:**
> IMHO I doubt you can have 2.6.1 of libc6-dev on Dapper without system breakage, As your talking about a lib that is three versions ahead of what your running, eg: it's included in gutsy.

You would need to upgrade a lot more then the lib in question as already said you would need to upgrade the gcc file among other files.

Your best off upgrading to next release.

As it seems in this post, having a 2.6.x versioned libc6-dev on Dapper is impossible. Any objections?

---

