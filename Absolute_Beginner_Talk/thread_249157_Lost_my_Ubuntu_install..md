---
title: "Lost my Ubuntu install."
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by el_escorpion on 2006-09-02
I have just installed windows Xp again, and now i can't see my Ubuntu install. I have tried seraching the forums and figured out that i need to reinstall GRUB. however, the methods proved don't work for some reason. I tried going into terminal and typing
"grub"
then when it comes up
"root (hd0,4)" (that is my root, partition)
but it gives me an error and says it doesn't exit. ](*,) 
If anyone is out there at this late hour please help.... i need my Ubuntu working by tommorow morning and so far in the past 2 hours nothing has worked.

---

### Post by davmac on 2006-09-02
You can find pretty detailed instructions for restoring grub at [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

Hope this helps,

Dave Mac

---

### Post by sailor2001 on 2006-09-02
installing windows over ubuntu doesn't work.....windows fornats the entire disk.....install ubuntu AFTER installing windows

---

### Post by el_escorpion on 2006-09-02
hmm, finally figured it out. If anyone has the same problem.. the general solution is the right one. However, something to keep in mind...
first line instead of just "grub" should be "sudo grub" as i was told most Linux distros have you running as root be default... Ubuntu isn't one of them. :P

well, it's all good now. thanks to the people who answered. :D

---

