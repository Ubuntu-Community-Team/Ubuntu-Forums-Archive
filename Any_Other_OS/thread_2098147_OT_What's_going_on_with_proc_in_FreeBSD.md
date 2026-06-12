---
title: "OT: What's going on with /proc in FreeBSD?"
date: 2012-12-25
forum: Any Other OS
---

### Post by Aaron Christianson on 2012-12-25
Not trying to start a flame-war here (don't even know if this is a hot-button issue), but I read on wikipedia (article entitled 'procfs') that FreeBSD is phasing out /proc. There wasn't really any explanation beyond that.

Does anyone know what they are actually doing and what their reasons are? While I'm not poking around /proc on a daily basis, it has its uses. Does it present a security risk, having such a link between kernel space and userspace? Are they creating another way to do somthing similar which doesn't utilize the file system? I know OS X gets along fine without one (well enough for the POSIX, in any event).

Links would be appreciated. This may be a bit overly technical for the Café, but I'm sure someone here knows the answer.

---

### Post by MadCow108 on 2012-12-25
the reasons are stated in the citation link, its simply not maintained (assuming its still valid)

must stuff in procfs is highly linux specific anyway and even there its not really a stable interface in all places
programs intended to be portable should not use it.

---

### Post by kk0sse54 on 2012-12-25
Procfs in FreeBSD has been deprecated for a while now. By default it doesn't mount /proc and the handbook suggests using sysctl instead. If you want to read a more recent debate on the issue there's this thread [http://lists.freebsd.org/pipermail/freebsd-fs/2011-February/010747.html](http://lists.freebsd.org/pipermail/freebsd-fs/2011-February/010747.html)

---

### Post by sffvba[e0rt on 2012-12-27
*Thread moved to **Other OS/Distro Talk**.*


404

---

