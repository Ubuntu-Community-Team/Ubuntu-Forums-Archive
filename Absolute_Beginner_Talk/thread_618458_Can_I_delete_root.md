---
title: "Can I delete root?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Howl01 on 2007-11-20
[[img=http://img90.imageshack.us/img90/4103/screenshotgv2.th.png]](http://img90.imageshack.us/my.php?image=screenshotgv2.png)

??

This is as I cannot save to folders or make new folders etc. in certain directories.

Can I therefore delete root?

I don't know the password for root...only my user account.

Any ideas?

---

### Post by AlexenderReez on 2007-11-20
your user account apssword is your root password....i suggest you wont disable root....because it will bring risk to your pc...

---

### Post by Inxsible on 2007-11-20
you can never delete root and still have access to your system.

The FIRST password that you created for your username during installation is the same as your root password.

Also, it is safer if you do not use root access unless you absolutely need to. and that too I would suggest using the sudo command at the terminal

---

### Post by aysiu on 2007-11-20
There's been a little bit of misinformation here.

The first user you create is not the root user, and the password for that user is not the root password.

The root account is a separate account that runs the system processes. If you delete this account, you will not have a working system. **Do not delete this account**. The root account is there for a reason.

That said, the root account is disabled for logins. You cannot, by default in Ubuntu, log in directly as root (recovery mode being the one exception... for recovery purposes), and there is no need to log in directly as root.

The first user created is in the *admin* group, which means she can temporarily assume root privileges for certain tasks if she prefaces those tasks with the command *gksudo*, *sudo*, or *kdesu*.

Read more about this here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

