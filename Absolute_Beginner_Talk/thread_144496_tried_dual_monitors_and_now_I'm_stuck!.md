---
title: "tried dual monitors and now I'm stuck!"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by chrluc on 2006-03-14
I tried dual monitors and didn't know or understand to backup the xorg.conf file and now x server is down. what are my options is there a way to keep my files if i have to reinstall. please help!

---

### Post by mlind on 2006-03-14
```

sudo dpkg-reconfigure xserver-xorg

```

will get revert your xorg.conf file.

Just accept all default values that configuration wizard suggests, 
if you don't know what they do. 

to restart your X server if you are using Gnome
```

sudo /etc/init.d/gdm restart

```

---

