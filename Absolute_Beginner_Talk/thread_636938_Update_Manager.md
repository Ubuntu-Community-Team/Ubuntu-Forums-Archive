---
title: "Update Manager"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by dgoodma on 2007-12-10
I am using xbuntu 7.10 on an older laptop, 128 MB memory, 900 MHz processor. It is working surprising well.

Update Manager says I have updates; when I go through the process to install, it does not consistently complete. It has with some updates, but it typically goes to sleep. I changed the ¨nice" setting to see if I could make the process wake up; but that did not help. I have DSL, so my network connection is good.

This is also true with Add Remove Manager, it has worked, but not always. Seems to just go to sleep most of the time.

---

### Post by SOULRiDER on 2007-12-10
Open a terminal and type these two commands.
```
sudo aptitude update
sudo aptitude dist-upgrade
```
That will alwars update your system with the latest packages.

---

