---
title: "Ubuntu went to login screen after random time"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by mmarif4u on 2008-03-06
I installed Ubuntu and was happy with it.
But today i experience the logging off problems with root and other users also.
My work is in the middle every time it went to log off screen.
it take random time,some time 5 min and some time 30min.

Any help???

---

### Post by justleen on 2008-03-06
do you have desktop effects enabled? If so,  try turning those off.

---

### Post by mmarif4u on 2008-03-06
Yup it was ON.
I change it to NONE.
One thing.i installed php and apache and mysql.
I change the root directory in apache to media/disk/www.
but every time the disk name changed according to 1st use of the drive.
So when it goes to login screen.It compiling in DOS mode and says media/disk/www 'No such directory'.and then goes to login screen.
Any idea about this.

---

### Post by kpkeerthi on 2008-03-06
You may also want to check if anything unusual is logged in .xsession-errors under your home directory...

---

### Post by justleen on 2008-03-06
make sure the /media/disk/ww actually exist, and that it is correctly mounted thorugh fstab, i'd say

---

### Post by mmarif4u on 2008-03-06
Yup it exists and working fine until that time.
Can i give a static disk name.Why it changes on every start after clicking.

---

