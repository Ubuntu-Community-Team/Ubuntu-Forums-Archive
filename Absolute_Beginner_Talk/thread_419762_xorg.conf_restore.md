---
title: "xorg.conf restore"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by l.j. on 2007-04-23
Ok i have about gave up on the nvidia driver. so i would like to restore my original xorg.conf file the backup is in my X11 directory i type [COLOR="Red"]cp etc/X11/xorg.conf.backup etc/X11/xorg.conf[/COLOR] it returns cp: cannot stat 'etc/X11/xorg.conf.backup': No such file or directory    I've booted to the live cd to view the directory i'm typing in case and everything both files are there any ideas.

---

### Post by taurus on 2007-04-23
```
sudo cp /etc/X11/xorg.conf.backup  /etc/X11/xorg.conf
```

---

### Post by Cypher on 2007-04-23
A good rule to remember is that anything outside of your home directory (/home/<username>) will probably require SUDO access. So if you get a funky error message, see if you need SUDO or not..

Regards

---

### Post by l.j. on 2007-04-23
Thanks been a long night lol

---

### Post by DracoPsycho on 2007-04-23
The mistake in the first post is that you have to begin path with / so it should be /etc/... and not etc/...

---

### Post by Cypher on 2007-04-23
> **DracoPsycho said:**
> The mistake in the first post is that you have to begin path with / so it should be /etc/... and not etc/...
Unless you're already at the "/" (root) level..:)

Regards

---

### Post by DracoPsycho on 2007-04-24
Right ;)

---

