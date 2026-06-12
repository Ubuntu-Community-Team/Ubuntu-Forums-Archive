---
title: "Mac 3,1 will not wake up from suspend when closed"
date: 2012-10-19
forum: Apple Hardware Users
---

### Post by jackdaniels123123 on 2012-10-19
My I recently updated my macbook pro 3,1 via software manager from 12.04 to 12.10. When I open the lid after putting it to sleep, all i see is the cursor and a black screen, nothing else. I have to restart the computer in order to use it again. i am using nvidia driver 304.51

---

### Post by 2F4U on 2012-10-19
It may be a problem with the nVidia driver. My MacBook 4,1 with Intel graphics suspends/resumes without issue. There is a special log file dedicated to suspend/resume:
/var/log/pm-suspend.log

It has all the steps performed during suspend/resume in it and may help to find which part fails.

---

