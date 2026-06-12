---
title: "need access to superuser account"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-05-18
is ther a step by step for this?

---

### Post by juxtaposed on 2007-05-18
You mean root?

Just log in as root from the login screen with the password you set for it when you installed ubuntu. If it says root can't log in from GDM or something, then you'll have to edit the log in screen settings (easily findable, just set it to allow the administrator to log in graphically).

Or you can do things as root from your account, like typing 'sudo nautilus', or 'gksudo nautilus' to have a graphical thing asking for your password.

Not sure if that is what you wanted...

---

### Post by taurus on 2007-05-18
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by wormser on 2007-05-18
It is better to use **sudo** instead of logging in as root.  If you really want/need to log into root then:

```
sudo passwd root
```

Now that you have created a password for root you can log in as root.

---

### Post by 99bluefoxx on 2007-05-18
ok did that
but when i tried it says administrator not allowed to logon from this screen
now what?
Edit: found the prob; allow admin logon box was unchecked
X_X

---

