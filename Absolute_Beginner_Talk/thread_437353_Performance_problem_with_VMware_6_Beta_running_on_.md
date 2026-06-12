---
title: "Performance problem with VMware 6 Beta running on Feisty-64 host"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by galileux on 2007-05-08
Hi I have a problem running 2 simultaneous WinXP hosts in the Feisty host running VMware Workstation Beta 6.0.
As soon as I power up the second VM everything slows down almost to standstill and I have to crash out of one of the VMs to regain control.

I believe this is unacceptable on a Core2Duo with 4GB RAM fully addressed by the host.

I posted this problem on the VMware forum, with further details, but so far I didn't get any reply that would point me to the right direction. Here is the link to the thread:

[http://www.vmware.com/community/thread.jspa?threadID=83605&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=83605&tstart=0)

Any help will be much appreciated, including proven alternatives to VMware...

---

### Post by galileux on 2007-05-08
Problem solved....
Do NOT set the number of processors to "Two", even if you have a Core2Duo.
Leave that value to "One"
Regards

---

