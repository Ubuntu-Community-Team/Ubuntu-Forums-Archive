---
title: "root password"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by dgs382 on 2007-06-22
Hi,

I am new to Linux and Unix although I have quite a bit of experience in Windows.  I just successfully installed Ubuntu Linux V7.04 on a new hard drive and using Wingrub was able to dual boot successfully.

However, whenever I try to do anything significant the system asks me for the root password.  The install did not ask for a root password, so I assume that a default root password was used.  How do I find the default root password?

Or, am I totally off track here and need to do a reinstall with different options?

Please assume I know nothing in your answers.

Thanks and best regards.

---

### Post by HereInOz on 2007-06-22
You actually use the password that you set up for yourself during the install.  You will learn more about this as time goes on :-)

---

### Post by wormser on 2007-06-22
Ubuntu does not set up a root password for security reasons.  Use **sudo** and **gksudo** (for gui apps) before the command.  So, do not set a root password... but for your knowledge...

```
sudo passwd root
```

Sudo and gksudo use your password.

---

### Post by dbbolton on 2007-06-22
> **dgs382 said:**
> Hi,

I am new to Linux and Unix although I have quite a bit of experience in Windows.  I just successfully installed Ubuntu Linux V7.04 on a new hard drive and using Wingrub was able to dual boot successfully.

However, whenever I try to do anything significant the system asks me for the root password.  The install did not ask for a root password, so I assume that a default root password was used.  How do I find the default root password?

Or, am I totally off track here and need to do a reinstall with different options?

Please assume I know nothing in your answers.

Thanks and best regards.
the root password is probably just the password you use to log in. but on debian, for instance, root has a different password.

if not, go to System > Administration > Users. it should ask for YOUR password. then click "show all users and groups". select the user called root, and then go to Edit. you can set 'root' password.

---

### Post by adza on 2007-06-22
the root user is disabled by default in ubuntu.... the user you created on install has root privs by using the command 'sudo' to run as root.. you will be then prompted to enter your password, the one you logged onto ubuntu with....

ie: sudo apt-get update (for example)

---

### Post by gizmoarena on 2007-06-22
in short, you do not have a root password
your password is the root password :)

and, you cannot install ubuntu with different options. ubuntu installation is one way 
*(unless you have an alternate cd)*

---

### Post by coffeecat on 2007-06-22
You might find [this page](https://help.ubuntu.com/community/RootSudo) from the Ubuntu Documentation useful.

---

