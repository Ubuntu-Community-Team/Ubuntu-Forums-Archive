---
title: "Package Manager"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by cssutto on 2006-04-22
Ubuntu 5.10

After installation, I ran the package manager for updates.

When I run package manager now, it tells me that it can not read the CD.

Since I have updated and the CD information is not as up to date as what is on the machine, what is the significance of this message and if it has none, can I get rid of the message?

Or am I missing something?

CSSJR

---

### Post by jorn on 2006-04-22
You can put a # in front of the cd entrance in your sources.list. That inactivates it.
Type or paste into terminal:
sudo gedit /etc/apt/sources.list
and save the file.

---

