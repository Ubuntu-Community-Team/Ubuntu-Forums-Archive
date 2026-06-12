---
title: "Resolution lost, gnome wont start"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by LordCthulu on 2008-02-04
For some reason,  Ubuntu booted into 640x400 resolution. I booted to my Winblows partition to get on here, and get help, and read some old topics. So I tried doing..
sudo dpkg-reconfigure xserver-org .. said xserver wasn't installed
I tried doing sudo /etc/init.d/gdm stop, it took me to a login screen, then tried starting x like 6 times. Didn't work, and gave me an error.

I tried /etc/init.d/gdm start, and it says something like "Start gnome   [ok]" but nothing ever happens. It takes me to something where I can setup my monitor/driver, but it won't find anything, and no matter what driver I try to pick it keeps using whatever is selected. When I first installed Gutsy, it said something about installing open source drivers for my vid card, so I did, and they worked great. I don't remember what it was called though, so I don't know how to select it from the list if it's even there.

---

### Post by spiderbatdad on 2008-02-04
not sure if you entered the right command, as it is wrong in your post.```
sudo dpkg-reconfigure -phigh** xserver-xorg**
```

---

