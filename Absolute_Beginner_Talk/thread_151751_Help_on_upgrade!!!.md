---
title: "Help on upgrade!!!"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by johnxxv on 2006-03-28
Help!

I am upgrading my ubuntu from hoary to breezy using a cdrom. But in the middle of the process of upgrading, my pc hang up. When I rebooted, only the login and password appeared only in texts without the graphics.

What should I do to view ubuntu again in graphics? I am having problems manipulating in the c prompt. Please help me.

---

### Post by Pragmatist on 2006-03-28
Try typing this:
```
sudo dpkg-reconfigure xserver-xorg
```

After that, read this:
[https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28upgrade%29](https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28upgrade%29)

---

### Post by johnxxv on 2006-03-28
It says that xserver-xorg is broken or not fully installed. What should I do?

Jo

---

### Post by mlind on 2006-03-28
does *sudo apt-get install ubuntu-desktop* work?

---

### Post by johnxxv on 2006-03-28
Thanks a lot!!!

I really appreciate it!

---

