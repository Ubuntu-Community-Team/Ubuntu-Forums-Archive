---
title: "Entering Runlevel One"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by ejoftiduttu on 2008-02-04
CAn anyone tell me how to enter into runlevel one..

---

### Post by Rocket2DMn on 2008-02-04
```
init 1
```
To get back
```
init 5
```
Why are you doing this anyway?

---

### Post by ejoftiduttu on 2008-02-04
Actually i dont know roots password. I need to change to runlevel one at boot time and change my root password

---

### Post by Rocket2DMn on 2008-02-04
Reboot the computer and at the GRUB screen select the Recovery Mode for your kernel.  Then run
```
passwd
```
Then you can reboot:
```
reboot
```
(who woulda thought up that command!)
Normally, the root password is the same password you setup your username with when you installed.

---

