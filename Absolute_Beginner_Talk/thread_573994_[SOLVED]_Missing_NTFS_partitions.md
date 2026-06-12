---
title: "[SOLVED] Missing NTFS partitions"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by camellochapin on 2007-10-12
Hi,

suddenly I can't access my two NTFS partitions, they are listed in my /media folder but they seem to be "empty", they don't show up in my "Computer" section at all.

Any help will be highly appreciated!

---

### Post by taurus on 2007-10-12
Try to mount them by hand and see what's the error message is.  Chances are you didn't shutdown your Windows properly so you can't mount those partitions with ntfs-3g (read/write).

---

### Post by Pumalite on 2007-10-12
More details. What's your OS?. Your specs. What were you doing right before this happened?

---

### Post by camellochapin on 2007-10-12
> **taurus said:**
> Try to mount them by hand and see what's the error message is.  Chances are you didn't shutdown your Windows properly so you can't mount those partitions with ntfs-3g (read/write).
Thanks a lot for your help!  Now I understand why "sometimes" I could see the NTFS partitions and "sometimes" I couldn't.

So, conclusion for everybody:  if you can't access your NTFS partitions... check if you just hibernated or turned off your Windows session!

Problem solved!

---

### Post by camellochapin on 2007-10-12
> **Pumalite said:**
> More details. What's your OS?. Your specs. What were you doing right before this happened?
Thanks for your help and concern, problem solved with the first hint I got!

---

### Post by martin.mev on 2007-10-18
OK! iam so fu*ked then :( cus i formated over my winxp partition. Anyone has the knowlage how to deal with that?

---

### Post by camellochapin on 2007-10-18
> **martin.mev said:**
> OK! iam so fu*ked then :( cus i formated over my winxp partition. Anyone has the knowlage how to deal with that?

what did you exactly do?

---

### Post by martin.mev on 2007-10-20
> **camellochapin said:**
> what did you exactly do?

well first i installed ubuntu 7.04. I did so by just reboot from windows and use the live cd. got to the ubuntu desktop and ran the installation. and when i got to the point where you get to setup where and how to isntall it i just used my 120GB hd where windows where installed. I picked the automatic way to install it, using the whole 120GB drive . after installation was done everything worked fine, the 400GB NTFS harddrive was mounted and worked. 

the day after this ubuntu 7.10 was released. so i downloaded it and this time i installed it with manual setup of the drive so i should get a partition for /, /home, and swap. when it was done installing the ntfs disk where mounted but i couldnt enter it w/o get some error msgs. and i remember reading something about a hibernation and windows in one of those error msgs. and now i dont even see the ntfs partition in my media folder :( 

So how can it talk about windows when it wasent even there when i installed it?

---

