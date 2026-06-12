---
title: "Is ther a way to update to the latest kernel 2.6.24.2 the &quot;standard&quot; way?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Fechter on 2008-02-18
I mean I don't have the time to download and compile the kernel... is there a way to update the kernel as I update my system through

sudo apt-get update
sudo apt-get upgrade

Can't I just add some lines to the sources.list or do a little trick and watch it work?

---

### Post by smartboyathome on 2008-02-18
No, there isn't. It could your break programs (since the programs are compiled for the 2.6.22 kernel), and isn't very safe for a newbie to do until hardy is released.

---

