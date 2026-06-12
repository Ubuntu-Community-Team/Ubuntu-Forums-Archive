---
title: "[SOLVED] How to mount a hard drive with cmd line"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by NR1224 on 2008-04-06
i have a partioned hard drive and a small 4gb fat32 partion is not shown in the graphical menus. I can see it in Gparted, but can't mont it in ubuntu. It is assigned /dev/hda2, so how would i go about monuting it. Again,  it is not showing up in the places menu so I need a command to mount it, thanks

---

### Post by scrooge_74 on 2008-04-06
sudo mount /dev/hda2 /mnt/someplace

---

### Post by NR1224 on 2008-04-06
thanx

---

