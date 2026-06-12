---
title: "Remove Apache2"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by mr_crimp on 2005-11-12
Hi, 

I've tried to install Apache2, PHP4 and php4-gd but I could'nt change the DocumentRoot to my Home dir. So I removed apache2, php4 and php4-gd with the "sudo apt-get remove apache2" command. That is apparently not enough. Apache2 is still running, also after reboot. How do I completely remove Apache2, PHP4 and all of its packages? The reason that I want to remove apache2 is that I want to install a totally clean version of Apache1.3.

I hope someone can help me.

---

### Post by matthewv on 2005-11-12
try removing the other Apache2 packages:
apache2-common
apache2-mpm-worker
apache2-utils
libapr0

---

### Post by mr_crimp on 2005-11-12
Thanks it's just working perfect. But it could'nt find the apache2-mpm-worker package but it's working anyway. 

In my /etc/init.d I have Apache2 should I delete this?

Thanks for your help...

---

### Post by matthewv on 2005-11-12
You shouldn't have to delete it, although I don't see why it would hurt. Alternatively, try ```
 sudo dpkg --purge {package names} 
``` to completely remove those packages and their config files

---

### Post by mr_crimp on 2005-11-12
Thanks...

---

