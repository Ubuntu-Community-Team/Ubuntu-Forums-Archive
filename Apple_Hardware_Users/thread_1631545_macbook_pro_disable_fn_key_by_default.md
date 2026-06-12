---
title: "macbook pro disable fn key by default"
date: 2010-11-26
forum: Apple Hardware Users
---

### Post by disappearedng on 2010-11-26
Is there a way to have fn key off by default in macbook pro? 

I really am not used to the fact that I have to press fn + ctrl + f4 to close windows nor fn-ctrl-f11 to maximize my screen.

---

### Post by theSuperman on 2010-11-26
On my Macbook in 10.10, running 
```
sudo su -c "echo -n 0x02 > /sys/module/hid_apple/parameters/fnmode"
```
enables F keys without needing FN. Must be run after each reboot.

---

### Post by wiznillyp on 2010-11-28
Are you using pommed?

If so, set the fn mode = 1, look at the write-up [here]("https://help.ubuntu.com/community/MacBookPro7-1/Lucid#Keyboard").

---

