---
title: "[SOLVED] kdevelop autoconf error"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by andrewoftheelves on 2007-10-11
hello, i am very new to programming, I have ubuntu studio mix. so i downloaded kdevelop through add/remove, and started it, went to new programms=>c++ =>  kde=> simple kde application, filled everything out, and then when i do build/ run automake and friends i get this message:

./admin/cvs.sh: 651: --version: not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

I tried installing autoconf through the synaptic package manager, but i still cant get it to work, if anyone could help i would greatly appreciate it.

---

### Post by andrewoftheelves on 2007-10-12
i realized that you just have to download a ton of libraries in order to compile yourself.ehh, kind of a problem for me, but im going to work at it until it well works..:)

---

### Post by xghstst0riesx on 2008-01-24
I'm running into the same problem. Any hints on what else I need to install? Thanks.

---

### Post by LarsO on 2008-02-12
Found this in another post and it worked for me:
sudo apt-get install libtool
sudo apt-get install automake

---

