---
title: "Diabling Bluetooth"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-06-04
presumably its possible to disable things one doesn't need. For example i don't use Bluetooth. Also, i 'm told i don't use Raid [don't even knowwhat it is] but it comes up as default i noticed in boot-up. 

So, the question is how can i disable stuff like that?

Allow me to thank you in advance,

--
sophtpaw

---

### Post by jvictor on 2006-06-04
sudo apt-get install sysv-rc-conf

sudo sysv-rc-conf

and remove the 'X' close to each service u dont need

HTH

---

### Post by evandec on 2006-06-04
Is there a guide to explain which services you are likley to not need. Also what do the service numbers at the top represent?

---

### Post by jvictor on 2006-06-05
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

