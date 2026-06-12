---
title: "[SOLVED] upgrading to latest version of gtkpod (not in repo)"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-09-02
Hello,
I would like to upgrade from version (0.99.8-0ubuntu3 (Ubuntu Feisty's repository package) to the newest version, 0.99.10.

From [http://www.gtkpod.org/news.html](http://www.gtkpod.org/news.html), I went to [http://www.gtkpod.org/downloads.html](http://www.gtkpod.org/downloads.html), then went to [http://www.getdeb.net/app.php?name=gtkpod](http://www.getdeb.net/app.php?name=gtkpod), then went to [http://www.getdeb.net/release.php?id=1128](http://www.getdeb.net/release.php?id=1128).

I clicked the [libgpod1 link]("http://www.getdeb.net/download.php?release=1128&fpos=1"), and had the deb file opened with GDebi Package Installer.
I then clicked the [gtkpod link]("http://www.getdeb.net/download.php?release=1128&fpos=0"), and had that deb file opened with GDebi Package Installer, too. 

But when I go to CLI and try running "gtkpod", I get this error message:
> gtkpod: error while loading shared libraries: libgpod.so.1: cannot open shared object file: No such file or directory 
How can we upgrade to the latest version of gtkpod?

---

### Post by macogw on 2007-09-02
check /lib for libgpod.so.1  You probably just need to install that library (look it up in Synaptic)

---

### Post by nonewmsgs on 2007-09-02
verified.  it is in synaptic.

---

### Post by hanzj on 2007-09-02
I don't see it in Synaptic (add/remove) nor in "sudo aptitude install  libgpod.so.1". 
Please advise.

---

### Post by nonewmsgs on 2007-09-02
Eek! i just went to upgrade mine and it doesnt like the gpod1 in the repositories BUT in the last link you posted there is a link to the new one that it does like.  it's right next to the gtkpod link.

---

### Post by hanzj on 2007-09-02
If you are talking about the  [libgpod1 link]("http://www.getdeb.net/download.php?release=1128&fpos=1"), i can't find   libgpod.so.1 inside the package. That libgpod1 package has the following files:
> 
./
usr/
usr/share/
usr/share/doc/
usr/share/doc/libgpod1/
usr/share/doc/libgpod1/changelog.gz
usr/share/doc/libgpod1/changelog.Debian.gz
usr/share/doc/libgpod1/README.gz
usr/share/doc/libgpod1/AUTHORS
usr/share/doc/libgpod1/copyright
usr/lib/
usr/lib/libgpod.so.2.0.0
usr/lib/libgpod.so.2



---

### Post by hanzj on 2007-09-02
After installing the 2 debs again, for some reason, it works now!
Thanks.

---

