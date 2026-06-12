---
title: "Format XP"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Janoubie on 2007-08-30
Hi all .. There is problem with xp .. I install it in a driver and UBUNTU install in other driver .. My problem is....
Now I want format windows and  install it agin ..Q : booting to ubuntu how now .. and how to return booting at the same in befor format ?

---

### Post by Janoubie on 2007-08-30
if there is no help it make more time to install xp and install ubuntu and update .. the connection for internet here slow may be 2 days to update ubuntu and return it like now .. plz help me

---

### Post by Hobo Joe on 2007-08-30
I'm a little confused as to what you're saying, could you be a little more specific, and explain your problem better?

---

### Post by Magneticgravity on 2007-08-30
Are Xp and Ubuntu in different partitons? If so, using your xp disc, you can delete the partition with Xp on.

---

### Post by Janoubie on 2007-08-30
Sir .. my problem is : I want to FORMAT XP and install it .. when i formatted i can't  inter to ubuntu .. they are in diffrent HDD .. problem how can i  inter to ubuntu and how can return booting dowl OS

---

### Post by Janoubie on 2007-08-30
how can LOGIN to ubuntu .. If i fromatt xp and install new one (XP)

---

### Post by Hobo Joe on 2007-08-30
Put in the Windows CD, and when it comes to the part about partitioning, then you can pick the appropriate partition.

Once you have it installed then you will need to re-install GRUB.

---

### Post by Janoubie on 2007-08-30
Ok how  re-install GRUB.

---

### Post by Hobo Joe on 2007-08-30
That will come after. Re-install Windows first.

---

### Post by Magneticgravity on 2007-08-30
Wipe both, then start over? hehe ;)

---

### Post by sdowney717 on 2007-08-30
if you reinstall XP, you need to boot the ubuntu live cd
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)
basically

open a terminal and type grub

type find /boot/grub/stage1         # this tells you where the root is and use this result for the next line

type root (hd1,0)         # this tells grub where root is for ubuntu, 1 is second drive, 0 is first partition
type setup (hd0)         # this sets up grub on xp primary drive
type quit to exit

---

### Post by Janoubie on 2007-08-30
THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... THANK ..THANK... 

It's Work

---

