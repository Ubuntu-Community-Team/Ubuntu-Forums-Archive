---
title: "vm server"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Doug11 on 2006-12-08
I tried to install vm server, but it keeps telling me that there is already a version installed. I have checked everywhere but do not see it. How can I find it and then get it to run if it is there?

---

### Post by scxtt on 2006-12-08
what do you get if you run **whereis vmware**? ... do you have anything when you do a **slocate vmware**? (may need to do a **sudo slocate -u** first) ...

---

### Post by Doug11 on 2006-12-08
Tried it, got this,,but could this be my "vm player"?


-laptop:~$ whereis vmware
vmware: /etc/vmware /usr/share/man/man4/vmware.4.gz

---

### Post by scxtt on 2006-12-08
you'd have more than just that, especially something in a "bin" directory ... AFAIK you can't have Player and Server installed @ the same time (and there's no real reason to) ... check for a script called **/usr/bin/vmware-uninstall.pl** and run it if you have it -- should erase whatever vmware related files you have (not VMs of course) ...

---

