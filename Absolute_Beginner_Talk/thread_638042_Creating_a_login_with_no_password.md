---
title: "Creating a login with no password"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by BattleGnome on 2007-12-11
Hi,

I have two users on this machine, myself and everyone else. For everyone else I have created a user called public. I would like to remove the password requirement from this user. How can I do this?

---

### Post by fedex1993 on 2007-12-11
i think if you go to system adminstration then user and groups find the user or user you want to modify and click properties and then there should be a password thingy. and all you half to do is remove the password for it

---

### Post by PinkFloyd102489 on 2007-12-11
Everytime Ive tried to do that, it complains about password length.

\

---

### Post by Dr Small on 2007-12-11
How about trying:
```
sudo passwd -d *public*
```

That should delete the user's password, from what the manual says.

Dr Small

---

### Post by jasonrandolph on 2007-12-11
If you can't get anything else to work, you can always set up your system to automatically login as you.  Whenever any user tries to change things at the SU level, it will password protect it.  The downside is that everyone will need to use your settings.

---

