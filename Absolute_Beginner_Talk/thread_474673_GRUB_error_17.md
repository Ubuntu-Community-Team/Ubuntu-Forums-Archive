---
title: "GRUB error 17"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Comcon on 2007-06-15
Hallo,
First of all i have two hard disks.
Recently i had install Ubuntu on my second one which is slave.
But yesterday i though that it would better if i had installed Ubuntu on my first one which writes at 7200 rpm unlike my second which writes at 5400 rpm.
So i format my second with [b]disk manager[b] but i left the Linux-swap partition unattached.
Now when i open my computer it is showing the following massage:
"GRUB Loading stage 1.5.
GRUB Loading,please wait
Error 17"
What i should do?
Thanks

---

### Post by confused57 on 2007-06-15
> **Comcon said:**
> Hallo,
First of all i have two hard disks.
Recently i had install Ubuntu on my second one which is slave.
But yesterday i though that it would better if i had installed Ubuntu on my first one which writes at 7200 rpm unlike my second which writes at 5400 rpm.
So i format my second with [b]disk manager[b] but i left the Linux-swap partition unattached.
Now when i open my computer it is showing the following massage:
"GRUB Loading stage 1.5.
GRUB Loading,please wait
Error 17"
What i should do?
Thanks
Grub's IPL on your first hard drive is looking for the next stage of grub, which was on your 2nd hard drive...you can restore your Window's IPL to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

or just install Ubuntu on your 1st drive, it should recognize your Window's install & add an entry in your menu.lst...be sure to defrag your Window's install, if you're going to resize it with the Ubuntu installer.

---

