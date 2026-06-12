---
title: "How do you change the resolution"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by M. Brown on 2005-10-13
How do you change the resolution.  It wont let me go above 1024x780  I'm sure this has been asked many times before but I forgot how to.

---

### Post by aysiu on 2005-10-13
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by Muhammad on 2005-10-14
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by M. Brown on 2005-10-14
I don't any pci buses or anything.  I am a complete noob.  also when I type in this code
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/xfree86/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg
```

It does absolutely nothing.

---

