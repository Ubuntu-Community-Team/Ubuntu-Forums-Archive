---
title: "WOOPS need help reseting users groups"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by BillGod on 2006-10-13
I was trying to add group disk to my user.  I tried usermod -Gdisk username.  now the only group I belong to is disk.  Kinda stuck here.  I cannot access anything and need to reset back to normal.  I am group root right now to get this far.  please help.

---

### Post by kidders on 2006-10-13
Hi there,

That's no problem to fix :-) You can use the same command to add yourself back into more groups. In addition to your own private group, Ubuntu probably added you to adm, dialout, cdrom, floppy, audio, dip, video, plugdev, lpadmin, scanner, admin. Not all of these memberships are necessarily terribly important though.

Hope that helps.

---

### Post by BillGod on 2006-10-13
ok cool those are the other groups i need.  how do i add them all to my user?    usermod -gbill -Gadm bill

will give me 2 groups but i do not know how to add more.  Thats how I got this issue in the first place  :)

---

### Post by BillGod on 2006-10-13
AHHH -a i got it.. thanks for your help

---

### Post by kidders on 2006-10-13
Hey again,

Yep, using -a adds (rather than overwrites) memberships. You should also be able to do things like **sudo usermod -G admin,audio,video bill**.

---

