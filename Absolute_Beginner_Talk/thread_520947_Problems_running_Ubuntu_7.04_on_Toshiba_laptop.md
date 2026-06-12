---
title: "Problems running Ubuntu 7.04 on Toshiba laptop"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by kevlar7 on 2007-08-08
I have a Toshiba Satellite P10-EE1 
Link for specs
 [http://www.toshiba.ca/web/product.grp?section=1&group=223&product=2391](http://www.toshiba.ca/web/product.grp?section=1&group=223&product=2391)

I am dual booting with XP. The installation went fine.(i think) When i try and log into Ubuntu it ask for my login name and password, then after i enter them in it looks like its going to load but it just freezes and all i get in desktop background and nothing else. Any suggestions would be helpful.

---

### Post by Al3xK3aton on 2007-08-08
Why not create a root account and log in as that instead? It's more likely to work, and it's more powerful anyway.

---

### Post by amazingtaters on 2007-08-08
Sounds like it's more than a problem with the account, though I guess it couldn't hurt to log on as root and find out. I can't think of anything off the top of my head to fix this, but I'll look around.

---

### Post by PriceChild on 2007-08-08
Please _NEVER_ log into X as root.

from the sessions menu bottom left, select "failsafe gnome", and then try to log in.

---

### Post by avmatso on 2007-08-12
I am having the exact same problem with a Toshiba P10. Changing the session to Failsafe GNOME did not help. Any other idea?

---

### Post by laidback on 2007-08-12
Use 640x480 video and see if that helps.
Does the live CD work?

---

### Post by avmatso on 2007-08-12
The destop image and the mouse arrow look correctly scaled; plus the right click doesn't work at all.  However, the live CD seemed to work OK.

---

### Post by kevlar7 on 2007-08-13
Logging in as Failsafe Gnome worked once for me, but i can't get to work anymore. The live cd seems to work just fine and screen resolution seems fine too. Also the write click doesnt work for me aswhile.

---

### Post by aseem_mal on 2007-08-18
I have had the same issue on my Toshiba A75. It freezes up.
I read on some other foum that it is an issue with the ATI display adaptors on Ubuntu.
Anyone found a solution yet?:confused:

---

### Post by jpmontalbo on 2007-08-18
has anyone tried acpi=off?

---

