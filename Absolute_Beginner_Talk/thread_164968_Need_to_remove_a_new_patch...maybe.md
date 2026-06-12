---
title: "Need to remove a new patch...maybe"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-04-23
I downloaded a patch (pmount_0.9.6-1~breezy1_i386.deb) and installed it with the command 'sudo dpkg -i pmount_0.9.6-1~breezy1_i386.deb' and I have lost complete use of my floppy drive.  Suggestions?

I just discovered that I now am also getting text transposed on top of other test.  Suggestions now?

---

### Post by Qrk on 2006-04-23
Since you installed it using dpkg, you can remove it via apt-get.
```

sudo apt-get remove pmount
```
should work.

I'd remcommend using synaptic to remove it (search for pemount)  as you can make sure you move the desired package.

---

