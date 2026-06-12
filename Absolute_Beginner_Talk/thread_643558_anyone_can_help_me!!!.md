---
title: "anyone can help me!!!"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by syareefdol on 2007-12-17
hey guys!im new linux user..just install it yesterdays!hah!removed my windows os and turn on ubuntu feisty fawn!so...here it goes!when i try to updates which are available..then an error occured!

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so..anyone can help me? ***..im quite blur about it..and really need help..but im willing to learn n play!!

---

### Post by spiderbatdad on 2007-12-17
quite simple...navigate to a terminal...Applications-->Accessories-->Terminal and enter the command ```
sudo dpkg --configure -a
``` You have a broken package. This will fix it.

---

### Post by sports fan Matt on 2007-12-17
Ive done the same when ive had broken packages..it does work quite easily..:)

---

### Post by syareefdol on 2007-12-18
thanx guys..but i try to install updates..the warning box came out..

Could not upgrade the system!
Fix broken packages first.

You have 1 broken package on your system!
Use the "Broken" filter to locate it.

any command??help me..thanx!

---

### Post by spai on 2007-12-18
> **syareefdol said:**
> thanx guys..but i try to install updates..the warning box came out..

Could not upgrade the system!
Fix broken packages first.

You have 1 broken package on your system!
Use the "Broken" filter to locate it.

any command??help me..thanx!

You can try synaptic package manager (It is located in system>admin>Synaptic)
In the bottom left corner of Synaptic, click on the 'custom filter' tab.
Then click on the 'broken' option. You will see some applications, fix 'em :)

---

### Post by philinux on 2007-12-18
sudo dpkg --configure -a

---

### Post by spiderbatdad on 2007-12-18
open synaptic package manager...lower left corner select "custom filters" then choose broken from the list upper left

---

### Post by hyper_ch on 2007-12-18
please use next time a descriptive thread title and not just a generic "need help" one.

---

