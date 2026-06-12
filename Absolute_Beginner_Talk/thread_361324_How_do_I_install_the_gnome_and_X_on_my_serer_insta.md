---
title: "How do I install the gnome and X on my serer installation?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by blake1 on 2007-02-14
Hi, i am on lynx at the moment on the 6.10 server edition of Ubuntu, and I dont know how to install X and gnome. I tried installing the X packages, but it kept asking for the cd. (I had enabled the universe repositries). Thanks in advance for your help!

---

### Post by Crooksey on 2007-02-14
sudo apt-get update
sudo apt-get install ubuntu-desktop

---

### Post by taurus on 2007-02-14
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by blake1 on 2007-02-14
I dont really want the full package, is there an "essentials" package or something, my HD is very small!

---

### Post by bodhi.zazen on 2007-02-14
[http://ubuntuforums.org/showthread.php?t=298818](http://ubuntuforums.org/showthread.php?t=298818)

---

### Post by blake1 on 2007-02-14
> **bodhi.zazen said:**
> [http://ubuntuforums.org/showthread.php?t=298818](http://ubuntuforums.org/showthread.php?t=298818)
Thanks for the link.

I have installed it all, but now xserver has an error.

```
Caught signal 11. Server aborting
Fatal IO error 104 (Connection reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.

```

How can I fix this?

---

### Post by taurus on 2007-02-14
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by blake1 on 2007-02-14
> **taurus said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```
I am still getting exactly the same error after going through that wizard.....

---

### Post by blake1 on 2007-02-14
Anyone have any ideas?

---

