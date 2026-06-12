---
title: "Dual booting vista and ubuntu with two harddrives"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by KwisatzHadarach on 2007-10-04
How would I go about doing this? Also, I thought about doing a setup with a dtdp switch so that each drive is completely seperate. Which would y'all recommend?

---

### Post by JawsThemeSwimming428 on 2007-10-05
No matter what, when you install Ubuntu UNPLUG YOUR VISTA drive. GRUB will destroy your VISTA MBR. You can use GRUB as your boot manager but if you want to use Vista you have to download a boot program. I used EasyBCD and it is pretty simple to set up. If you do overwrite your Vista MBR (I did) pop in  the Vista disk and go into recovery environment. It is very easy to restore.

---

