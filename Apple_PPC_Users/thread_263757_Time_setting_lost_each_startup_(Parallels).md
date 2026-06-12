---
title: "Time setting lost each startup (Parallels)"
date: 2006-09-23
forum: Apple PPC Users
---

### Post by geodude on 2006-09-23
I've install Ubuntu in Parallels on my Macbook Pro. The correct time zone is selected in the Time prefs. I syncronize the time once to get the clock set. the next time I boot the clcok is 4 hours behind. Repeat setting, reboot, it's off again.

Anyone else seeing this or offer a sugegstion to fix?

---

### Post by jd65pl on 2006-09-23
Boot your computer and enter the BIOS settings (usually by pressing [DEL] but differs between machines). Check the clock there see if it is also wrong.

J

---

### Post by hajk on 2006-09-24
This is a known problem with running Linux in a virtual machine, Parallels or otherwise. There is an approximate work-around that will see the Ubuntu clock never more than about 10 seconds off the OS X clock, as per my notes on installing Ubuntu in a Parallels VM on a MacBook (see sig). An exact solution will have to wait for Parallels making Parallels Tools also available for Linux...

---

### Post by geodude on 2006-09-24
Thanks. I will have to look at these directions more, it's all  "greek" to me. :-)

Your write up talks about the clock in the VM being fast. My issue is the clock is exacly four hours slow. I'm asuming the fix will work in either case?

Again, thanks for the write up. I was going to ask about screen resolution next!  :-)

---

### Post by hajk on 2006-09-24
> **geodude said:**
> Thanks. I will have to look at these directions more, it's all  "greek" to me. :-)

Your write up talks about the clock in the VM being fast. My issue is the clock is exacly four hours slow. I'm asuming the fix will work in either case?

Again, thanks for the write up. I was going to ask about screen resolution next!  :-)

*Exactly* four hours slow seems like a timezone configuration issue, I'm also showing in my notes how you can set the time to local (as in OS X).

---

### Post by geodude on 2006-09-24
The issue was fixed by editing  /etc/default/rcS

Thanks!

---

