---
title: "Time sync problem"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by qpackard on 2006-04-15
Running dual boot with ubuntu 5.10 and win xp sp2, using GRUB to choose os.

When I sychronize in Windows and change to linux the clock is 6 hours away. When I sychronize in linux and change to win the clock there is 6 hours off. In win I'm at MST (GMT -7) and in ubuntu I am at America/Denver.
When I'm booting linux the clock sets but fails to synchronize with ntp.ubuntulinux.org.
Is there a way to control this perverse behavior? (The clock's, not my dual-booting.)
Perhaps I should synchronize in only one os?

:-?

---

### Post by ubernoob on 2006-04-15
The problem is that linux thinks the hardware clock is set to universal time and do the offset by 6 hours in the system to get your local time. Windows alway sets your clock to local time. So you need to change it in linux. You get that option when you install ubuntu. But i can't find where to change it now. :(

---

### Post by astoltz on 2006-04-15
Edit the file /etc/default/rcS and change the line that reads:

UTC=yes

to UTC=no

---

### Post by confused57 on 2006-04-15
I had the same problem, used this thread to get the times sync'd:

[http://www.ubuntuforums.org/showthread.php?t=123004](http://www.ubuntuforums.org/showthread.php?t=123004)

---

### Post by CELI-Nux on 2006-09-07
Just tried it and checking if this will work!!!  Please do not reply to this post (sorry)

Regards.

---

