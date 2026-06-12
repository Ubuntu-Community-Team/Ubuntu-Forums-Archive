---
title: "help? deleted admin account cant do anything"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by ironslave on 2006-09-13
i was trying to figure a way to get full acces to my PC and tried making a new admin account and deleted the old one.... the new admin account... well isnt admin anymore... and i cant do anything except get online.... i cant get root acces with anything ive found..... how can i regain control of my account?

---

### Post by fiver22 on 2006-09-13
Look at this thread: [http://ubuntuforums.org/showthread.php?t=241964](http://ubuntuforums.org/showthread.php?t=241964)
-does that help you? -it helped me. 
Please respond.

---

### Post by codejunkie on 2006-09-13
> **ironslave said:**
> i was trying to figure a way to get full acces to my PC and tried making a new admin account and deleted the old one.... the new admin account... well isnt admin anymore... and i cant do anything except get online.... i cant get root acces with anything ive found..... how can i regain control of my account?

reboot the computer at the grub menu choose the recovery mode usually it's the second option in the grub menu it will boot up into a terminal only mode with root access.

once you get to the terminal you can add your user account to the admin group by entering ```
adduser yourusername admin
```

or you can enable the root account with```
passwd root
```and enter a new root password, now reboot by pressing ctrl+alt+delete and login like you normaly would, and you can gain root access by opening a terminal and enter```
su
```and enter the new password you just set.
now run ```
users-admin
``` and it will open the user control panel so you can make the changes to your account.

---

### Post by ironslave on 2006-09-13
thanks that last post did the trick....

---

