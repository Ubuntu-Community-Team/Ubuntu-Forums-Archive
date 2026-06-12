---
title: "[SOLVED] Slow internet!!"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by jaredssix on 2008-01-17
Hey all,
 I just helped my friend install a dual boot system with XP and Gutsy.
He can connect to the internet by ethernet and wireless, but both are extremely slow.

Perhaps ipv6? Other suggestions?

Thanks in advance!

---

### Post by Udaho on 2008-01-17
Try disabling ipv6 in Firefox:

Open Firefox and type "about:config" in the address bar without the quotes.

In the Filter box type "network.dns.dsableIPv6" without the quotes and when it appears on the list double click it to set its value to True. Exit and restart Firefox.

---

### Post by Udaho on 2008-01-17
Meant to say type "network.dns.disableIPv6", forgot a letter in the previous post.

---

### Post by jaredssix on 2008-01-17
Thanks!
I solved by thread [http://ubuntuforums.org/archive/index.php/t-87798.html](http://ubuntuforums.org/archive/index.php/t-87798.html) suggestion of:

"There's an easy way: instead of changing aliases file, create fie named bad_list in /etc/modprobe.d containing this line:
alias net-pf-10 offNow reboot and voila, no IPv6 on your system!

This method will work even if /etc/modprobe.d/aliases get replaced at some update."

Thanks again!

---

### Post by jaredssix on 2008-01-17
And then I used your tip on another friends computer, which worked perfectly (and proves simpler to implement).

Thanks a ton!

---

### Post by jaredssix on 2008-01-17
Thanks . . .

---

