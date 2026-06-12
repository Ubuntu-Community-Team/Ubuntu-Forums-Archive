---
title: "Upgrading Gaim to Beta 5"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by milad on 2006-11-29
I'm using Amarok as my audio player in Ubuntu and it has a "Now Playing" script which enables you to show information about the song you're playing in Gaim's away messages. However, it seems to work only with the latest version of Gaim, which is beta 5.

So as the pre-installed version in Edgy is Beta3.1, I tried to upgrade it to the latest version myself. I downloaded the .rpm file and converted to a .deb one using alien.

and here's my first question, which doesn't have anything to do with this problem:
Do you have to remove the current version of a software if you want to install a newer version from a deb file? Or does the installer automatically overwrites the current version?

now back to the problem, I uninstalled Gaim using Add/Remove and then installed it from the deb file, but it didn't work.
Anyone knows a better way to upgrade gaim?

Personally I don't care about using the latest version of Gaim, what I'm looking is the "Now Playing" plugin for Amarok, or any other audio player, so if you know any other way to make it work please let me know.

---

### Post by PriceChild on 2006-11-29
I've just built mine from source... downloading tarball, extracting,
```
./configure
make
sudo make install
```I don't advise alien

---

### Post by ryu kun on 2006-11-29
Click [here]("http://neoaddict.wordpress.com/2006/11/10/build-gaim-200-beta-5-from-source/") to learn how to build gaim 2.0.0 beta5 from source

---

### Post by milad on 2007-03-24
[This]("http://ubuntuforums.org/showthread.php?t=359466&highlight=gaim+beta") finally helped me through the installation.

---

