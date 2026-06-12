---
title: "MacBook Will not RESTART"
date: 2010-03-28
forum: Apple Hardware Users
---

### Post by bhj6268 on 2010-03-28
Yes I recently bought a White Unibody MacBook!  I installed Ubuntu 9.10 and for some reason it will not restart!  I can tell it to shutdown and it does perfectly.  When I click restart it will either go black but the screen is still on or it states it's restarting and just sits like that without ever actually powering down!  Can someone help me?

---

### Post by llamabr on 2010-03-28
and what do you get if from the terminal you do:

```
sudo shutdown -r now
```

---

### Post by bhj6268 on 2010-03-28
Same thing, the screen goes blank but the computer still didn't power down!

---

### Post by linuxopjemac on 2010-03-29
which model you have ?

under OSX; either click in OS X on the Apple on the top left, then "About this Mac" -- "More Info...", see the generation in the "Model Identifier" row; or run in a terminal:

```
sysctl hw.model
```

under Ubuntu; you can find out what model and generation you have, by typing at the terminal:

```
sudo dmidecode -s system-product-name
```

---

### Post by bhj6268 on 2010-03-30
It's the MacBook6,1

---

### Post by linuxopjemac on 2010-03-30
[https://help.ubuntu.com/community/MacBook6-1/Karmic#Reboot](https://help.ubuntu.com/community/MacBook6-1/Karmic#Reboot)

---

