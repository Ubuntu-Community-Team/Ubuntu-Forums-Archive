---
title: "cp: omitting directory ??"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by nbv4 on 2007-06-14
nbv4@nbv4:/media/Stuff$ cp Music\ Collection/ /media/disk/
cp: omitting directory `Music Collection/'

I'm trying to move a folder from ome disc to another, but I'm getting this error. I don't think it's a permission thing. What gives? I can move other files from that drive with no problems. Is it because of the space in the directory name? How can I work around this? I can't just rename it because /media/Stuff is a read only NTFS filesystem (/media/disk is ext3)...

---

### Post by ggaaron on 2007-06-14
cp -R

---

