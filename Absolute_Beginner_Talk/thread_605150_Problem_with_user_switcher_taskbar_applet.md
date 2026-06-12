---
title: "Problem with user switcher taskbar applet"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by meanburrito920 on 2007-11-06
for some reason when I try and switch back to a logged in user the screen turns white and even though the mouse is still movable I have to restart X to get things working again. so far I have only noticed it on the User Switcher applet, it works when i switch to a not logged in person. any ideas on what went wrong?

---

### Post by meanburrito920 on 2007-11-06
It also happens when i try and log out. I basically cant switch users at all except the first time per X reboot.

---

### Post by meanburrito920 on 2007-11-07
anyone have any ideas?

---

### Post by feedmecereal on 2007-11-07
I've just started having this same problem. I've noticed that I can type the password and it logs in fine.

---

### Post by CharlieFoxtrot on 2007-11-08
Same here. White screen when I try to switch back.

---

### Post by CharlieFoxtrot on 2007-11-08
Think I found something. It may be a conflict with compiz.

I disabled compiz (system>preferences>appearance>visual effects>none) for each user and rebooted to make sure that I was starting clean. I was then able to switch users without problems. Then I re-enabled compiz for one user and switched users. When I tried to switch back to the first user, I "white screened". Disabled compiz again, rebooted and user switching works normally.

Can anyone confirm?

---

### Post by CoffeeDaze on 2007-11-13
Go into preferences in the User Switcher applet and uncheck the "Lock the screen after switching users" option. You will have to do this in all user accounts and it should solve your problem.

---

### Post by fatejudger on 2007-11-13
It would be nice to get a fix that doesn't involve disabling user locking. Any ideas?

---

### Post by CoffeeDaze on 2007-11-13
Type in the password of the account as mentioned above.

---

