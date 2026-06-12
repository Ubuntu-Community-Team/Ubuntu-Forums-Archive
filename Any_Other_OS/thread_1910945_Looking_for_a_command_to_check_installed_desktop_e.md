---
title: "Looking for a command to check installed desktop enviornments"
date: 2012-01-18
forum: Any Other OS
---

### Post by tech291083 on 2012-01-18
Hi,

I have used Fedora for some time and I use the following command in a shell to know which deskstop environment I am running now. 


```
**find /usr/share/xsessions -name "*.desktop" -exec basename "{}" .desktop ";"**
```

```
echo $DESKTOP_SESSION
```

Is there a way I can do the same in Ubuntu 10.10 or later? How do I get a list of all the desktop enviornments that I have installed (suppose that I install other DEs such as KDE, Xfce etc.)? Is there a particular file that keeps track of it? Thanks.

---

### Post by Toz on 2012-01-24
Both of those commands work fine in my 11.10 install. The first command lists all installed sessions (as far as I can tell) and the second command displays the current session.

---

### Post by bluexrider on 2012-01-24
> **Toz said:**
> Both of those commands work fine in my 11.10 install. The first command lists all installed sessions (as far as I can tell) and the second command displays the current session.

Using 11.04 and this works for me too

---

