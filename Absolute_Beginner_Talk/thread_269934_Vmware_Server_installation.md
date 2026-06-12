---
title: "Vmware Server installation"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by mercerm on 2006-10-02
Hi Everyone,
I had a version of vmware player that i installed using automatix. I am now trying to install vmware server. I uninstalled vmware using synaptic and ./uninstall-vmware.pl both seemed to go ok and said completed successfully but when i try to install vm server is errors out saying a previous version has been detected. Is there a file i might have missed?? Any help is greatly appreciated. I'm pulling my hair out over this. 
Thanks

---

### Post by mitch.c on 2006-10-02
I've had this happen before when tyring to install vmware server after a failed installation. I was able to solve by deleting /etc/vmware (folder and contents). Perhaps this will work for you.

---

### Post by mercerm on 2006-10-02
That worked!! thaks alot.

---

