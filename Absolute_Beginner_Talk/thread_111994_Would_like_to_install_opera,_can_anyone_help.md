---
title: "Would like to install opera, can anyone help?"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by RavenRidge on 2006-01-03
Hi,
I have run many distros on this buddy of mine and this is the one!
Finally I feel like I am home. I work as the computer guy and a
dozen area libraries and am the one to call in our little corner
of Vermont if you are having trouble with your windows system.\
I would like to install opera I have set up universe, multiverse
backports and none have opera which does have a linux version.
I also down loaded snes and don't know what to do with it. I guess
I am in need of learning how to install outsde of apt-get.
Thanks
Bill

---

### Post by Zelut on 2006-01-03
easiest way is to add the opera repository to your list.  If you add this:

> deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

to your etc/apt/sources.list you'll be able to install opera.

NOTE: for some reason this doesn't add a menu listing.  You'll have to create the menu manually.  The file is located in /usr/bin)

more reading here... [https://wiki.ubuntu.com/OperaBrowser?action=show&redirect=Opera](https://wiki.ubuntu.com/OperaBrowser?action=show&redirect=Opera)

---

### Post by RavenRidge on 2006-01-03
Thanks a million!!!!
Bill

---

### Post by carlosqueso on 2006-01-03
Which snes did you download, and did you use apt/synaptic?  I used snes9x and zsens, both of which are in the repositories.  Let me know if you still want help.

---

