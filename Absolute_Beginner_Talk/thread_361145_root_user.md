---
title: "root user?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-02-14
i am logged in as the main user, because i can change the theme and other stuff that require a password, but i can't enter gdmsetup

how do i log in as a root user?

---

### Post by ajmorris on 2007-02-14
in a shell type ```
sudo gdmsetup
```

This will ask for a password. Do not be fooled by the fact that no characters or asteriks appear. Nothing is supposed to appear to indicate the password is being typed in, but it is.

---

### Post by pebo on 2007-02-14
Have you read [this]("https://help.ubuntu.com/community/RootSudo")?

---

### Post by aysiu on 2007-02-14
Instead of ```
sudo gdmsetup
``` you probably want ```
gksudo gdmsetup
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

By the way, you don't need to run the command in order to do that. Just go to **System > Administration > Login Window** and enter your password.

---

### Post by panti19 on 2007-02-14
i want to change the splash screen and i read that's the only place i can do that :)  thanks

---

### Post by aysiu on 2007-02-14
> **panti19 said:**
> i want to change the splash screen and i read that's the only place i can do that :)  thanks
**Which "splash"?**
The *splash* screen? You mean that appears *after* you log in? Or you mean the splash that appears when you boot-up? Or do you mean the background image at the login screen?

**Login Splash**
If you mean the one that appears after login, then you have to change that manually. I believe the file to replace is in /usr/share/pixmaps/splash

To modify system files, this may help you:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

**Boot Splash**
If you mean the one that appears during boot-up, this may help:
[http://doc.gwos.org/index.php/Change_Usplash](http://doc.gwos.org/index.php/Change_Usplash)

**Login Screen Background**
And, of course, if you mean the background image that appears at the login screen, then you're absolutely correct: System > Administration > Login Window is the place to change that.

---

