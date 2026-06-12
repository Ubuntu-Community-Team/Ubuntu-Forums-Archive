---
title: "xorg.conf"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by JParkus on 2007-07-27
I was told to remove xorg.conf to fix a problem i was having now with it missing i cant truly enable the restricted drivers so i can use beryl while i figure out compiz fusion .

how do i add a new xorg.conf file ?

---

### Post by kevinlyfellow on 2007-07-27
> **JParkus said:**
> I was told to remove xorg.conf to fix a problem i was having now with it missing i cant truly enable the restricted drivers so i can use beryl while i figure out compiz fusion .

how do i add a new xorg.conf file ?

You never want to just get rid of xorg.conf, but isn't it cool how it starts up anyways?

To get back the original file 
```
sudo dpkg-reconfigure xserver-xorg -pcritical
```

---

### Post by dfreer on 2007-07-27
ummm. I cannot see any reason to completely remove xorg.conf, that sounds like bad advice to me. EDIT: although, if you truly wanted to remove it, it would've been better to back it up, and then removing the original file

you can try this command:
```
sudo dpkg-reconfigure xserver-xorg
```
To generate another /etc/X11/xorg.conf file

---

