---
title: "re-installing gutsy in &quot;/&quot; partition"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by A.Bruce on 2008-03-16
Hello, i recently installed gusty on my laptop and since i anticipated screwing things up i made a seperate partion for "/home" and "/" as i was advised to do. Sure enough i screwed it up and my question now is how do i reinstall ubuntu only onto the / partion without disturbing my /home files?

---

### Post by bsharp on 2008-03-16
When you are installing, (let's say your root partition is sda1) select "/" to be included on sda1 and (assuming your /home is sda2) select your /home to be mounted at sda2, but do not format it.

---

### Post by A.Bruce on 2008-03-17
Thanks!

---

### Post by forrestcupp on 2008-03-17
Right.  Each partition will have a check box next to it to format.  Make sure you don't check the one that is /home.

You will probably have to do a manual partition.  Just select your root partition and you'll have to edit it and set the mount point as root again and check the format box.

Then you'll have to select the /home partition, edit it, and set the mount point as /home and *do not* check the format box.

You'll be ok.

---

