---
title: "Installing xvidcap"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by jigglemaster7 on 2007-05-17
Can someone guide me to installing xvidcap so i can record videos

---

### Post by jigglemaster7 on 2007-05-17
Can someone guide me to installing xvidcap or if there is a .deb that would be great ( im a noob)

---

### Post by kinematic on 2007-05-17
```
aptitude install xvidcap
```

---

### Post by embrik on 2007-05-19
There are no xvidcap in the regular repositories. DO you know a repository containing xvidcap?

---

### Post by StitchJAcket on 2007-11-27
> **kinematic said:**
> ```
aptitude install xvidcap
```

Correction it's
```
sudo aptitude install xvidcap
```

---

### Post by Kallewoof on 2007-12-23
*meep* Wrong answer... but thanks for the fish. :/

Edit: googling it seems xvidcap *WAS* a part of ubuntu but was.. removed? I have multiverse enabled and all that but despite links like [1] it's not there.

[1] [http://archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcap/](http://archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcap/)
/Edit.

> $ sudo aptitude install xvidcap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "xvidcap"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      


---

### Post by harold4 on 2007-12-23
apt-cache search xvidcap returns

```
xvidcap - Screen video capture for X

```

Post your /etc/apt/sources.list if you can't find it.

[Download]("http://sourceforge.net/project/showfiles.php?group_id=81535&package_id=83441&release_id=512201")

---

