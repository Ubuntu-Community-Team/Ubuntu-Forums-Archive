---
title: "update problem"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by jackss on 2006-03-24
hi, i have the next problem: when i try "sudo apt-get update" i get this error:
Fetched 6927kB in 2m11s (52.5kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

can sombody helpme

---

### Post by pbaehr on 2006-03-24
It doesn't seem like it should work but if I remember right I got that message once and ran sudo apt-get update again "to correct these problems" like it suggested at the end. To my surprise it fixed it.

---

### Post by edopizza on 2006-03-24
Type 

sudo gedit /etc/apt/sources.list

Check if you have twice the lines that are reported as dublicated

---

### Post by jackss on 2006-03-24
thanks it works

---

