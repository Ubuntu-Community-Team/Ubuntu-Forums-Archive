---
title: "unmount hardrives"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by DamagePlan on 2008-01-26
On my desktop im stuck with some drives which I want to unmount so I can get rid f the m of the desktop. When I unmount I get thsi message:

You are not privileged to unmount the volume 'HP'.

How could I sort this out?

THanks

---

### Post by taurus on 2008-01-26
Open a terminal and see what is the name of the mount point for that drive.  

Applications -> Accessories -> Terminal
```
df -h
```

Then, unmount it with

```
sudo umount /media/HP
```
Assuming /media/HP is the name of the mount point.

---

### Post by DamagePlan on 2008-01-26
It says it busy..

---

### Post by taurus on 2008-01-26
Are you in that directory or if something is accessing it?  Make sure you close nautilus first.

---

### Post by DamagePlan on 2008-01-26
Sorry, im not that good with linux but what is nautilus?

Other than that I have closed everything. Still says Its busy.


Thanks,
DP

---

### Post by Tteddo on 2008-01-26
If you just want the space on your desktop launch the configuration editor (gconf-editor) and click apps->nautilus->desktop, then uncheck volumes_visible. That will turn off the display of mounted volumes. They will still be in computer though, and on the Places menu.
There's all kinds of other settings in there too.

---

