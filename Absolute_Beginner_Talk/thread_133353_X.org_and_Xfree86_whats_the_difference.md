---
title: "X.org and Xfree86 whats the difference?"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by adambeazley on 2006-02-20
Whats up people,
Im new to linux and im just trying to figure out which ati driver to download. The one fore X.org or Xfree86?? Which comes with ubuntu and is installed by default and what are they? I know they both have something to do with te x-server desktop, but I would love it if someone can take the time to explain it to me.
thanks,
Adam

---

### Post by zi99y on 2006-02-20
I'm newish too and wondered this myself recently. I believe ubuntu ships with Xorg, which is a modified version of xfree86, although development is still ongoing with both systems. 

If you reconfigure X using "dpkg-reconfigure xserver xorg" then you are using xorg, if you do "dpkg-reconfigure xserver-xfree86" then you will be using xfree86!

I first had this confusion when installing debian (on another machine) and it seems to use xfree86...

(hope I got that right - if not I'm sure someone will be here to correct me soon)

---

### Post by pravuil on 2006-08-22
Xfree86 did something with their license which made a bunch of linux distros switch to xorg. Your stuck with Xorg in Ubuntu.

---

### Post by mostwanted on 2006-08-22
Xorg is a fork of Xfree86 because of changes made in the licensing on behalf of the Xfree86 copyright holders. Since Xfree86 isn't really relevant for Linux anymore (only older distro versions use it now), you can just view Xorg as a newer version of Xfree86.

---

