---
title: "Auto Login V Security"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by MarkX on 2008-01-22
If one uses auto-login what are the security implications (apart from the computer being accessible if stolen or someone messing about on it in person while you're not there) ? Is there a possibility of it getting hacked etc. from the net?

---

### Post by meborc on 2008-01-22
> **MarkX said:**
> If one uses auto-login what are the security implications (apart from the computer being accessible if stolen or someone messing about on it in person while you're not there) ? Is there a possibility of it getting hacked etc. from the net?

apart from the obvious - your sister messing with your computer, there is no other threat... since logging in to linux as your normal user does not give the user any root privileges. IF you would create a root password (which i do not recommend) and use root login automatically, then it would open your computer to all kinds of hacks

so NO :D using a auto-login with your normal user will be the same as to log in to the computer yourself

---

### Post by MarkX on 2008-01-22
> **meborc said:**
> apart from the obvious - your sister messing with your computer, there is no other threat... since logging in to linux as your normal user does not give the user any root privileges. IF you would create a root password (which i do not recommend) and use root login automatically, then it would open your computer to all kinds of hacks

so NO :D using a auto-login with your normal user will be the same as to log in to the computer yourself

Aha! Thing is that us noobs just use the one user and password from install (which presumably IS the root one?) and don't bother creating new users. So I should  create a new user and use that for auto login, yes?

---

### Post by meborc on 2008-01-22
> **MarkX said:**
> Aha! Thing is that us noobs just use the one user and password from install (which presumably IS the root one?) and don't bother creating new users. So I should  create a new user and use that for auto login, yes?

no, thats the beauty of ubuntu... you DON'T have a root account... you have your normal user account, which you can assign root permissions with "sudo"

so you don't need to do anything... you can safely use your account for auto-login

this explains a bit more about root and sudo - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by MarkX on 2008-01-22
Super-duper, I get it, thanks!

---

