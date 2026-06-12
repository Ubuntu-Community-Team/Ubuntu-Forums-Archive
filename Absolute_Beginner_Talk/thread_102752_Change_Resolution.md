---
title: "Change Resolution"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by Maupertus on 2005-12-12
When I installed Ubuntu I accidentily hit enter without properly configuring the resolutions I wanted Ubuntu to be able to use.

Now I like a 1280*960 res. But as I didn't put an asterix in that box during install, I can't use it.

How do I change this little problem?

---

### Post by Turtle.net on 2005-12-12
Just post your xorg.conf (/etc/X11/xorg.conf) and we will try to help you :)

---

### Post by nikopol on 2005-12-12
sudo dpkg-reconfigure xserver-xorg
will reconfigure it for you.

---

### Post by aysiu on 2005-12-12
Your solution lies within: [http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

