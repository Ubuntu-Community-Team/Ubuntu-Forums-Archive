---
title: "What to do with extra .deb packages..."
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-07-19
Hi, I just installed the fglrx driver but now I have like 4 or 5 .deb packages on my desktop.I don't know if I should move them or what please help.

---

### Post by reacocard on 2006-07-19
.deb files are software packages, like installer exe's in windows. if you're done installing them, go ahead and delete them.

---

### Post by Klemik on 2006-07-19
sudo dpkg -i package.deb

---

### Post by Kilz on 2006-07-19
> **Klemik said:**
> sudo dpkg -i package.deb
Yes that will install them, but after they are installed you can delete them like reacocard said.

---

### Post by mattisking on 2006-07-19
I also like the package gdebi (available in the repositories - Synaptic). Once installed, you can actually double click a deb that's on your desktop and immediately install it.

---

