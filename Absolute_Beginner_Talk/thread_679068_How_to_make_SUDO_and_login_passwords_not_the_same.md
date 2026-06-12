---
title: "How to make SUDO and login passwords not the same"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2008-01-26
Can it be done so that the login password in different than the sudo password.

I tried to take away admin privilages from a user but then accessing some options is a pain. If I assign admin privilages then everybody can login and knowing the login password can also execute SUDO.

How can somebody login and not be able to execute SUDO meaning that sudo password is not the same as login.

Thanx!!!!!!!!!!!

---

### Post by taurus on 2008-01-26
As long as you don't add that user to group admin, he/she can't run sudo.

---

### Post by shad0w_walker on 2008-01-26
I think a command better suited to your needs would be

```
su
```

It switches you temporarily to a different user and requires that users password instead of the current users. So you can switch to a more privileged account to work when you need to.

---

### Post by bagrol1 on 2008-01-26
Well, I want to be able to have only one user so I don't have to create another setup for my wife.

If I have to create a new account for my wife how do I "the look" of my desktop quickly to new user so don't have to spend hours creating it from scratch.

> **taurus said:**
> As long as you don't add that user to group admin, he/she can't run sudo.

---

### Post by bagrol1 on 2008-01-26
OK, please explain how to do it. I'd like my wife to be able to log in but not change anything important.  But if I check out admin access for myself then many options under administrative tasks are not shown and I have no clue how to get to them.

> **shad0w_walker said:**
> I think a command better suited to your needs would be

```
su
```

It switches you temporarily to a different user and requires that users password instead of the current users. So you can switch to a more privileged account to work when you need to.

---

### Post by shad0w_walker on 2008-01-26
Thinking about this more, I assume you only have one the one user and will just log straight into that. Why don't you just setup autologin so when the computer is turned on it will login then you don't have to bother telling anyone you don't want to the password.

---

### Post by bagrol1 on 2008-01-26
Because often I have to do  CTRL ALT DEL to refresh Gnome and then pass is needed. Also when I go to standby after waking up it asks for password.

> **shad0w_walker said:**
> Thinking about this more, I assume you only have one the one user and will just log straight into that. Why don't you just setup autologin so when the computer is turned on it will login then you don't have to bother telling anyone you don't want to the password.

---

### Post by shad0w_walker on 2008-01-26
It's control-alt-backspace to restart X. Not ctrl-alt-delete. And you can set a timed login so after 10 seconds it will automatically log in again if something happens.

---

### Post by mcduck on 2008-01-26
> **bagrol1 said:**
> Well, I want to be able to have only one user so I don't have to create another setup for my wife.

If I have to create a new account for my wife how do I "the look" of my desktop quickly to new user so don't have to spend hours creating it from scratch.

All your personal settings are stored inside your home folder, in hidden files (all files/directories with a name starting with a dot are hidden, press Ctrl-H to see them in the file manager). Just copy those files to the new user's home (and then change their ownership so that the new user owns them) and she'll get exactly the same desktop configuration you have now.

---

### Post by bagrol1 on 2008-01-28
Thanks all for your help!!!

The best solution I found out is to have one account without admin privilages and then second root account where you don't even have to type sudo for everything - the login into root can be enabled in the security settings.

This is probably the best **unless** there is a way to have a two tiered password system, say one password valid only for login and second password working for sudo.

Please advise!

---

### Post by emarkd on 2008-01-28
Be very careful using a true root account.  With the current setup you at least get a password prompt to warn you that you're about to do something potentially dangerous.  If you really login as root, you'll get no warning and Linux will do whatever you tell it without second-guessing you.  Make sure you're ready for that.

---

### Post by anaconda on 2008-01-28
You dont have to enable root acount.. here is an alternate way to have a separate password for sudo..

[http://ubuntuforums.org/showthread.php?t=181877&page=2](http://ubuntuforums.org/showthread.php?t=181877&page=2)

---

