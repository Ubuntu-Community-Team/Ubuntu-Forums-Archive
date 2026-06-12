---
title: "Possible to use Swap post-install?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by rj686 on 2007-01-15
I created a  swap partition post install because I just installed suspend2 into my kernel. How do i utilize it now? does swap go in fstab? Does anyone know all the commands for suspend2, i know of "sudo hibernate" but no others.

---

### Post by jordanmthomas on 2007-01-15
Yes, you should put it in /etc/fstab
```
/dev/sda2               swap                    swap    defaults        0 0
```
The relevant line from my gentoo installation.  You'd need to change sda2 to whatever it needs to be though.
If you just want to enable the swap without rebooting
```
sudo swapon /dev/sdx
```

You can see what suspend2 installed on your system by right clicking on it in Synaptic.
The stuff it puts in /bin or /sbin are executables usually

---

### Post by anaconda on 2007-01-15
Did you also remember to actually make your swap partition to be swap? if not do::
mkswap /dev/sdaX

(just change sdaX to point to your swap partition.."sudo fdisk -l" will tell you which is your swap if you dont know it already..)

---

