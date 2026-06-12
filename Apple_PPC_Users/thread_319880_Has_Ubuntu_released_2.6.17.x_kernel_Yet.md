---
title: "Has Ubuntu released 2.6.17.x kernel Yet?"
date: 2006-12-16
forum: Apple PPC Users
---

### Post by markpoole@ntlbusiness.com on 2006-12-16
Hi need some help on different levels. 

1.) new to terminal a need to get to root terminal on dapper alternate followed directions from stmiller to no avail. Seems I do not understand the use of a sudo? 

2.) not to bother with this process would like a link to stmiller's other point that unbuntu may of released a kernel to solve the cooling fan problem!

Will make a 3D name tag for any one who can help!

---

### Post by stream303 on 2006-12-16
If you just need to quiet the fans, you can do so with the existing kernel after you suffer through the noisy install.  Once you get to a desktop:

sudo -s
cd /lib/modules/$(uname -r)/kernel/drivers/macintosh
ls | cut -d. -f1 | xargs -n1 modprobe
lsmod | cut -d" " -f1 | grep windfarm >> /etc/modules
exit

This will quiet your fans immediately, and keep them quiet from then on even after rebooting.  Don't forget the period after -d. in the third line.

If you are running a G5 iMac, you may also want to take a look at:
[http://wiki.debian.org/iMacG5](http://wiki.debian.org/iMacG5)
from torrance

---

