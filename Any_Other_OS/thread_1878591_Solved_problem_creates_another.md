---
title: "Solved problem creates another"
date: 2011-11-10
forum: Any Other OS
---

### Post by myolbug on 2011-11-10
Ok, to start, I ran into some video problems and I was generously helped by hailtothethief. [http://ubuntuforums.org/showthread.php?t=1873773](http://ubuntuforums.org/showthread.php?t=1873773)

However, now, I have an issue with starting the oos up.  Instead of it going onto the normal start up mode, it looks like it will start, the the screen goes black, like I told it to when I stopped gdm, but i get this instead:
Linux Mint9 Isadora Minty-Fresh tty1Minty-Fresh Login:

So far, the only way I can get past this is to run the commands in the thread again and then sudo service gdm start.

What went awry and how do I get it to boot normally again?

---

### Post by myolbug on 2011-11-10
Anyone have any ideas?

---

### Post by dolphin194 on 2011-11-10
I would recommend that you uninstall your desktop manager and re-intall it.

For example:
```

sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

```
if you're using Ubuntu, or
```

sudo apt-get remove xubuntu-desktop
sudo apt-get install xubuntu-desktop

```
for Xubuntu, and so on.

---

### Post by Mark Phelps on 2011-11-10
Since this is, apparently, a problem in Mint, have you tried the Mint forums:

[http://forums.linuxmint.com/]("http://forums.linuxmint.com/")

---

### Post by Perfect Storm on 2011-11-10
Moved to Other OS/Distro Talk.

---

### Post by myolbug on 2011-11-19
Is there actually anyone on this forum?

---

