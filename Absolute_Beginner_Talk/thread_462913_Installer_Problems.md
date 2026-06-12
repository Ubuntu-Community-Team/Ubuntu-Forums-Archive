---
title: "Installer Problems"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Barry Smalley on 2007-06-03
I am new to Ubuntu and Linux.

I have been using it for seven days and am slowly making a full transition. I have now arrived at a stumbling block that will not allow me to install any software or updates.

I have tried to install Jokosher and the install got corrupted.

Every time I try to install now I get this message

E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory

I deleted the Lock File and removed the Jokosher archive and replaced it with another one. No matter what I do I cannot clear it and am at the verge of a complete new reinstall of Ubuntu.

Can anyone help with some fix.

---

### Post by meng on 2007-06-03
Did you try:

sudo dpkg --configure -a

---

