---
title: "Can't install after a failed attempt of installing Second Life"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-05-26
After a failed attempt of installing Second Life, I tried to install ubuntu-desktop but...
```
...  xli xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl
  xvncviewer yelp zenity
0 packages upgraded, 311 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 723MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the secondlife-install package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

```

---

### Post by rohan! on 2007-05-26
i had same  problem agter attempting to install from the deb file.

i managed to reinstall secondlife from the deb file
```
sudo dpkg -i Desktop/secondlife-install_1.16.0.5-1~getdeb1_i386.deb
```
which has fixed the problem.

---

