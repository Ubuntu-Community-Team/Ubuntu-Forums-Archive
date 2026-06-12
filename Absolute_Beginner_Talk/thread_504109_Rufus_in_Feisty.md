---
title: "Rufus in Feisty"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by kikkymorra on 2007-07-18
HI!

I have just upgraded from edgy to feisty, and tried to install my favorite BitTorrent client, Rufus... Firstly from a .deb file - there is a dependency problem with Python - after being able to see it in Synaptic PM as a broken package, I saw that it requires Python 2.4.x, but **not** 2.5 or later. On the other hand, too much stuff depends on Python 2.5 to experiment with its removal.
Then I tried compiling from source, mostly by following instructions from
[http://linux-facile.blogspot.com/2007/07/installer-rufus-sur-ubuntu-704-feisty.html](http://linux-facile.blogspot.com/2007/07/installer-rufus-sur-ubuntu-704-feisty.html)
and
[https://help.ubuntu.com/community/Rufus](https://help.ubuntu.com/community/Rufus).
Eventually, the installation seemed successful, but the Rufus would still not start - it constantly reported a missing wx module it had failed to load.
After playing with installations of various wx* stuff, I think I found the right thing having installed python-wxtools and python-wxversion, both version 2.6.3x, and the Rufus finally worked - up until the update of python-wxtools and python-wxversion - after which it reported the same failure to load the missing wx module.
Does anyone know a way of getting Rufus to work without having to downgrade these packages?

Thank you.

Cheers-

---

