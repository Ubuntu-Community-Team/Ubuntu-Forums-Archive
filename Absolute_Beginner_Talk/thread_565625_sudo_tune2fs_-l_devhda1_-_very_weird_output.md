---
title: "sudo tune2fs -l /dev/hda1 - very weird output"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-02
This is strange - please see attached - dont seem right.

---

### Post by ajgreeny on 2007-10-02
Why not?  The output is almost exactly the same as mine and I've been using tune2fs to set fsck timing etc for some time now with various linux installs.  What exactly did you expect to see from this command and why did you use it?

---

### Post by philinux on 2007-10-02
Well the check interval is six months. I dont think thats normal for a fresh install

---

### Post by ajgreeny on 2007-10-03
I think it is set as 6 months unless you set it as something else lower than that.  You will also see that the Mount count is at 22 and that the Max mount count is 28, therefore in another 6 boots it will go into a filecheck (fsck) at bootup.  Mine also says the same but I've set my system to check every 80 boots, if I don't decide to do it manually before that point.

---

