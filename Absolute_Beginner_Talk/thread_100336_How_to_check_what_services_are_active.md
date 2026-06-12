---
title: "How to check what services are active?"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by CYHPT.net on 2005-12-07
Hi all,

Im new to linux, and esp to ubuntu. Can someone tell me how wud I check what services (http, ftp, ssh, telnet... etc) are active or that are already active? I wanna know the command to check a list of services that are started.

Thanks

---

### Post by ChrisTheGeek on 2005-12-07
Hi,

If you're running breezy (v5.10), you can go to System->Administration->Services.  Anything in that dialog with a check mark next to it is currently running.  

The scripts that control the services can be found in /etc/init.d.  These scripts are run when services are started and stopped and can be used from the command line to manually restart services if required.

Hope this helps,
Chris

---

### Post by CYHPT.net on 2005-12-07
Thanks,

So If Web server, DNS, etc are not shown that means that I havent installed it, right?

---

### Post by Rackerz on 2005-12-07
It might mean that, or it might mean they just haven't been started.

---

### Post by timsch75 on 2005-12-07
type "top" at the command prompt.  It gives you a great amount of information on running processes.  to exit the program, type "q"

---

