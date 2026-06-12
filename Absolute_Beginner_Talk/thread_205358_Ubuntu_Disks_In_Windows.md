---
title: "Ubuntu Disks In Windows"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by shoot2kill on 2006-06-28
i currently dual boot with XP and ubuntu.. i can see all three HDD's that are in my computer within Ubuntu, but cannot see my Ubuntu HDD within windows... can this be done..

???????????????????????????

---

### Post by aysiu on 2006-06-28
Yes: [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by xtacocorex on 2006-06-28
Natively, Windows cannot see Ext2/3 partitions.

[http://www.fs-driver.org](http://www.fs-driver.org) will allow you to see those partitions from within Windows. I've used it minimally, but it seemed to work very well.

Edit:
aysiu beat me to it.

---

### Post by shoot2kill on 2006-06-28
[QUOTE=aysiu]Yes: [http://www.fs-driver.org](http://www.fs-driver.org)[/QUOTE]

tyhanks for the fast reply, but when using this softare all i see when i open the drive in explorer, is (see screenshot)

---

### Post by xtacocorex on 2006-06-28
This is going to bug me now. I don't know what could be wrong, but I do have some theories.

1) Improper Character set, not using UTF or something like that
2) Improper drive setup
3) Didn't restart to get the changes to take affect
4) The drive filesystem isn't Ext2/3, it's something else like ReiserFS or XFS
5) Could be a bug in the driver

I'm not at my wife's computer where I installed it so I can't take a look at browsing my external harddrive to see the configuration.

---

### Post by shoot2kill on 2006-06-28
im not at the stated computer anymore.. when i go back on it, maybe later, maybe tomorrow, i will have another look..

thanks again for help

---

