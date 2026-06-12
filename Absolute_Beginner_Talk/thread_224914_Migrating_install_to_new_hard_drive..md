---
title: "Migrating install to new hard drive."
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by laraby on 2006-07-28
I currently have 2 drives in my PC, one XP and one Ubuntu.  I would like to swap out my ubuntu one for a larger. is it possible to migrate my install to the new drive? ( I can remove the windows drive temporarily to transfer the install, but do need to keep it)

Thanks for any help!

---

### Post by tseliot on 2006-07-29
moved to a more appropriate section

---

### Post by rowanparker on 2006-07-29
Yes it is possible (I think).
You need to have the old drive in and your new one in (remove the windows one). Boot Ubuntu (If it doesn't boot, use the LiveCD and just mount root filesystem) and copy / to the new drive, change your /etc/fstab now if you need to. Then take out the old drive and put windows drive back in (the same place where you got it from). Boot Ubuntu as normal (I hope).


Rowan.

---

### Post by aysiu on 2006-07-29
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

