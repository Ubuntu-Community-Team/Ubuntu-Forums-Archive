---
title: "Lack of Display/Resolution Options"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by wkupike2000 on 2006-09-18
I'm a new Linux convert(or will be) and ran 5 different live cd of different distro's this weekend. Ubuntu was by far my favorite but was the only one that gave me the 1024 x 768 as the best option when I normally run at 1280 x 1024. The other 4 all gave me that option and I tried to figure out a way to do it but had no luck. So before I install something other than Ubuntu, any help for a newbie correcting this?

Thanks!

---

### Post by bodhi.zazen on 2006-09-18
Try this.

On the live CD open a terminal and type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If that does not work, look at an xorg.conf from the other distro's, particularly the monitor and screen sections.

---

