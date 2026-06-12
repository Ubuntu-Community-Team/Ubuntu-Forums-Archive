---
title: "ld renamed"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by sys_alpha on 2008-02-12
hi,
  i am facing a big problem .
 I arbitrarily renamed the file ld-linux.so.2 (while reading the a.out file i found the entry /lib/ld-linux.so.2) :( in /lib  and then rebooted. After this my ubuntu 6.06 says ..
    Mounting root file system
    Waiting for root file system ....
and then it  hangs (does nothin)..


Please Help me.

---

### Post by jhenager on 2008-02-12
use your live CD to get back into the system and rename the file again.

---

### Post by smartboyathome on 2008-02-12
Boot up the live disk and rename the file back to what it was origionally named. Then it should boot properly. :)

---

### Post by sys_alpha on 2008-02-12
i did that ,but that does not help .
it says ..
waiting for root file system and hangs .....

---

### Post by DJ_Peng on 2008-02-13
Have you taken any kernel upgrades since you installed? If so there may be a few different versions to boot into on your Grub menu. Make sure the newest one (highest numbered one) is what you're booting into. Earlier today I was working on a Usplash and was getting that error. It turns out it was trying to use an older kernel. Once I specified the newer one it booted up like it should.

---

### Post by sys_alpha on 2008-02-13
no i didn't .
The only t6hing i did was plugging out the bus going into HDD in order to replace that. Nothing Else.

---

### Post by sys_alpha on 2008-02-13
ohh,,
after googling a while i found the solution.
the root file system was transported to /dev/hdc1 so i edited the files  /boot/grub/menu.lst and /etc/fstab  accordingly.

Thanks for the answers.

---

### Post by DJ_Peng on 2008-02-13
That was going to be the next thing I suggested. Hopefully the DIsk Manager tool coming to the next version of Ubuntu (sorry, I can't think of what it's called) will help fix that. But that won't be available until at least April.

---

