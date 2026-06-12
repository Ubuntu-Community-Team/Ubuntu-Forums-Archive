---
title: "F4l"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-01-01
Hi,

Could someone please tell me the sudo apt-get command to install Flash For Linux please if that's possible?

---

### Post by az on 2006-01-01
Package flashplayer-mozilla

    * breezy (web): Macromedia Flash Player [multiverse]
      7.0.25-0.0ubuntu1: i386

Package flashplugin-nonfree
     * breezy (web): Macromedia Flash Player plugin installer [multiverse]
7.0.25-5: i386


I usually use the flashplayer-mozilla package which fetches the latest package from the net, but sine the version was updates, it no longer seems to work.  Use flashplugin-nonfree.  You need to enable the universe repository
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

