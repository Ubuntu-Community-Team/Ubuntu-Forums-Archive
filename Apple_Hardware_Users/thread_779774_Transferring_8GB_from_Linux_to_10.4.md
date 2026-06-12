---
title: "Transferring 8GB from Linux to 10.4"
date: 2008-05-03
forum: Apple Hardware Users
---

### Post by uberlinux on 2008-05-03
HELP!
Transferring a 8GB .dmg from an Ubuntu 8.04 workstation to a macbook running 10.4 OS X is always erroring out using cyberduck on the mac to sftp into the linux worstation.  It always errors out at exactly 2Gb.  Anyone have any ideas for getting this .dmg from The linux workstation to the macbook?

---

### Post by billbear on 2008-05-03
Try the built-in FTP share in OS X

---

### Post by uberlinux on 2008-05-03
I'm going the other way, from Linux to macos.  I just ended up raring the .dmg.  Just so long as everything re-assembles fine, this is solved.

---

### Post by hyper_ch on 2008-05-03
does mac osx have no rsync?

---

### Post by 50words on 2008-05-14
> **hyper_ch said:**
> does mac osx have no rsync?

I would like to know the answer, as well. Is there a version of rsync for OSX?

Looks like yes, but with some issues: [http://patternbuffer.wordpress.com/2007/12/04/a-history-of-rsync-on-mac-os-x/](http://patternbuffer.wordpress.com/2007/12/04/a-history-of-rsync-on-mac-os-x/)

---

### Post by cyberdork33 on 2008-05-14
> **50words said:**
> I would like to know the answer, as well. Is there a version of rsync for OSX?

Looks like yes, but with some issues: [http://patternbuffer.wordpress.com/2007/12/04/a-history-of-rsync-on-mac-os-x/](http://patternbuffer.wordpress.com/2007/12/04/a-history-of-rsync-on-mac-os-x/)
I would think you could install rsync with macports or the like.

---

