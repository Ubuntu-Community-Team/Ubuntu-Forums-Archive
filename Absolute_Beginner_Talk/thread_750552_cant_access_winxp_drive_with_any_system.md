---
title: "cant access winxp drive with any system"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by alnhntr29 on 2008-04-09
I posted this 2 times already and no response. I have a drive that has winxp on it. I have several ubuntu distros and none of them will mount the drive at all. The latest one is kubuntu/8.04/kde 4.0
I am trying to get bluetooth gprs internet working and the stuff I need is on the xp drive, its the only one I can get online with. When I boot into kde and try to access the drive it says mount refused, uid=1000. How do I mount the drive so I can get the stuff off of it?

---

### Post by Sidewinder1 on 2008-04-09
If you can see the drive in Nautilus, you should be able to right click on it and then select mount. If that doesn't work perhaps someone more knowledgeable than I can assist you.

---

### Post by Tatty on 2008-04-09
Ok lets try to mount the drive via the CLI

Can you post the output of ```
sudo fdisk -l
```

---

### Post by alnhntr29 on 2008-04-09
I cant easily do that, I have to be on the xp drive to be online. I have to bbot into kde and then hand copy everything and then type it here after rebooting into xp. What I can tell you is that the disk is recognized and listed, but when I try to open it, I get fixed mount refused, uid=1000

---

