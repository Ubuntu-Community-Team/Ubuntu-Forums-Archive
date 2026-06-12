---
title: "root?"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Robotuner on 2007-01-30
Hi, I'm new to Ubunto, new to linux. When I installed Ubunto 6.1 on my laptop, it asked me for a login name and password, so I entered one. After installation, I was poking around in the networking dialogs and got a dialog saying I had to be logged in as root to access the dialog. I didn't enter a password for root, only for my login. So, heres my question, am I the admin or a user with limited rights? and what password do I enter when I logon as root? BLANK doesn't work.
 
Thanks

---

### Post by taurus on 2007-01-30
The actual root account is disable but since you belong to groups adm & admin, you can use sudo or gksudo to execute those programs.  You just use the same password that you log in with.  Here's more info about it.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by K.Mandla on 2007-01-30
You should use the same password you use to log on to your machine. The first user account will have priviledges to run root-level applications. It's a [safety feature]("https://help.ubuntu.com/community/RootSudo").

Edit: So. We meet again, Taurus.

---

### Post by Maestro23 on 2007-01-30
> **Robotuner said:**
> Hi, I'm new to Ubunto, new to linux. When I installed Ubunto 6.1 on my laptop, it asked me for a login name and password, so I entered one. After installation, I was poking around in the networking dialogs and got a dialog saying I had to be logged in as root to access the dialog. I didn't enter a password for root, only for my login. So, heres my question, am I the admin or a user with limited rights? and what password do I enter when I logon as root? BLANK doesn't work.
 
Thanks

This should shed some light: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taurus on 2007-01-30
> **K.Mandla said:**
> 
Edit: So. We meet again, Taurus.

Yes, master.  ):P

---

