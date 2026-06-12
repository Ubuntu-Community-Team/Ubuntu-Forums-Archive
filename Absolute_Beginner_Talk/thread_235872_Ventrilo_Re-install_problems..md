---
title: "Ventrilo Re-install problems."
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Catewilliams on 2006-08-13
I just recently installed Ventrilo through wine, it was working perfectly, and if there was any problem, it was most likely my own computer.
Then I wasn't able to hear people, at all. I did what I could with my computer and the Vent settings, but nothing seemed to help, so I decided to try and re-install it.

The problem is, when I first installed it, I didn't have to do anything. wine did it all for me. Now, when I try to re-install Ventrilo, it asks me if I want to modify it, repair it or uninstall it- even though Ventrilo doesn't show up anywhere on my computer. 

Would there be a reason for this, and is there any way to fix it? - Thanks.

---

### Post by Cynical on 2006-10-08
I know this is old but I just ran into this problem and I wanted to leave an answer for anyone else who is looking. 

Navigate to /home/username/.wine
Open system.reg, user.reg, and userdef.reg and clear any entries relating to ventrilo.
Delete the ventrilo folder in program files and run the installer again.

---

### Post by Catewilliams on 2006-10-21
> **Cynical said:**
> I know this is old but I just ran into this problem and I wanted to leave an answer for anyone else who is looking. 

Navigate to /home/username/.wine
Open system.reg, user.reg, and userdef.reg and clear any entries relating to ventrilo.
Delete the ventrilo folder in program files and run the installer again.


Sir, Ma'am, you get an internet for this. :]
This is perfect, I tried and its working top notch. WHOO!

---

