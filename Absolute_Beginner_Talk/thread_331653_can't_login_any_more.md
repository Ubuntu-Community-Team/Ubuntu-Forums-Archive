---
title: "can't login any more"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-01-04
hi all,i cant login to edgy ,i fixed my xserver and resolution but now i cant login,
i cant login to the failsafe mode but i can get into the terminal part...

---

### Post by MkfIbK7a on 2007-01-04
what happens when you try?

---

### Post by STREETURCHINE on 2007-01-04
it just recycles to the login screen again..

---

### Post by STREETURCHINE on 2007-01-04
bump  :D

---

### Post by STREETURCHINE on 2007-01-05
re'bump

---

### Post by macogw on 2007-01-05
recycles to the login screen?  is your hard drive full by any chance?  that seems to be common symptom of a full hard drive

---

### Post by zmuth734 on 2007-01-05
> **macogw said:**
> recycles to the login screen?  is your hard drive full by any chance?  that seems to be common symptom of a full hard drive

yep: [http://ubuntuforums.org/showthread.php?t=329349](http://ubuntuforums.org/showthread.php?t=329349)

what do you get when you type **df -h**  after pressing <ctrl><alt><f2> at the login screen?

---

### Post by STREETURCHINE on 2007-01-05
hard drive not full.new installation of edgy no tweaks except trying to get the resolution fixed.

thanks for your replies ,but after blundering around for ages reconfigureing this and that and a brocken xserver i found a very simple solution which i shall post next.
 thanks for the effort

---

### Post by STREETURCHINE on 2007-01-05
here is how i fixed my problem,could not login because my xserver was crashing when trying to login.
 
so i thought i have a perfectly good xorg.conf on hda1 running dapper ,with good resolution

 so i did not know if it would work ,i mounted hdb1

then i copied my xorg.conf from dapper and pasted it in my xorg.conf on hdb1 edgy.

and rebooted.
i now hav good resolution and can login ,it works....:D

---

