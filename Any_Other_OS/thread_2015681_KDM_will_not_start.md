---
title: "KDM will not start"
date: 2012-07-03
forum: Any Other OS
---

### Post by Quantumstate on 2012-07-03
I am at my wit's end.  I can not figure out this infernal upstart system.

Just installed BackTrack and encrypted the disk.  It always boots to CLI by default.  So I installed KDM but apparently it is not familiar with the new upstart system either because it will not start on boot.  It puts symlinks in init.d and it even puts a .config in init.  And I can start it with service start kdm.  

But it will not start on boot.  Why did they foist this on us right as I am trying to learn BackTrack?!

---

### Post by la_tupac on 2012-07-03
What about using rc.local ?

---

### Post by Quantumstate on 2012-07-03
I guess I'm going to have to.  This command is supposed to enable an upstart service at boot:
chkconfig kdm on
... but unfortunately it needs /sbin/insserv which is no longer there!  Brilliant!

---

### Post by oldos2er on 2012-07-03
Moved to Other OS/Distro Talk.

---

### Post by Quantumstate on 2012-07-03
Yup, now there's no hope of finding an answer;  moved to the sticks.

---

