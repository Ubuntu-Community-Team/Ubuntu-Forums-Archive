---
title: "Can enable ATI restricted drivers but xorg.conf does not exist"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by grebarton on 2008-01-12
Trying to install ATI driver for my HD 2600 card but the steps say i need to get this problem sorted out first.

The restricted drivers come up as enabled but not in use. Then when I try to change any of it it says my xorg.conf file does not exist. I checked this and sure enough its nowhere to be seen.

I have tried following many tutorials and guides to set this up so may have accidentally messed up along the way but i simply cannot get this to work.

---

### Post by dcstar on 2008-01-12
> **grebarton said:**
> Trying to install ATI driver for my HD 2600 card but the steps say i need to get this problem sorted out first.

The restricted drivers come up as enabled but not in use. Then when I try to change any of it it says my xorg.conf file does not exist. I checked this and sure enough its nowhere to be seen.

I have tried following many tutorials and guides to set this up so may have accidentally messed up along the way but i simply cannot get this to work.
In a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
will make a new file.

---

