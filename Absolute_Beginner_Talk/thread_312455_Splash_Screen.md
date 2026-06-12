---
title: "Splash Screen"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Jussi01 on 2006-12-04
I just uninstalled kubuntu, and now just running straight ubuntu edgy. However I still get the kubuntu splash on start up - not the login just the splash - can someone help me change it back to ubuntu?

---

### Post by Paul41 on 2006-12-04
Open a terminal and type :
```
sudo update-alternatives --config usplash-artwork.so
```

Select the usplash you want (ubuntu or kubuntu) and press enter then type :
```
sudo dpkg-reconfigure linux-image-`uname -r`
```

The above is from the following post.
[http://ubuntuforums.org/showthread.php?t=247668](http://ubuntuforums.org/showthread.php?t=247668)

---

### Post by Jussi01 on 2006-12-04
Thanks, but like the guy in the other post, I got an error message...

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.

Do you know how to fix it?

---

### Post by Jussi01 on 2006-12-06
All Sorted!!! Just did the second command after the error and it fixed it!! Cheers!!

---

