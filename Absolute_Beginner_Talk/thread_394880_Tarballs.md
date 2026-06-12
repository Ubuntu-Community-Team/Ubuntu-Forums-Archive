---
title: "Tarballs"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Tunica Intima on 2007-03-27
I just installed ubuntu and after having problems with the default network manager, I downloaded wifi-radar as I read it was supposed to be really good, but problem is I have no idea how to install a tarball, specifically wifi-radar. I tried the install guide text file that came with it but I quickly found myself way over my head.

---

### Post by charles.g.moore on 2007-03-27
I know that wi-fi radar is in the repos
sudo aptitude update
sudo aptitude install wifi-radar
It will be in your menu under internet

If you want to use the tarball
tar -xvzf wifiradar.tar
ls
cd into directory made
./configure
sudo make
sudo make install

If i were you id grab it off the repos though

---

### Post by Tunica Intima on 2007-03-27
Thanks, I could fianlly install it. Unfortunately I cant get an ip address.

---

### Post by charles.g.moore on 2007-03-28
I installed it yesterday before you posted and had no problems with it, but after about an hour I started to get kicked off intermittently (nothing to do with the wifiradar) so I tried to mess with the wifiradar and screwed everything up.

Ended up just going back no network manager until I can do some more research...

---

