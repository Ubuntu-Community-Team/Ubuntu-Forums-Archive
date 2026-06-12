---
title: "Username/password at start - needed or not? [Resolved]"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by jamienos on 2007-03-06
I have an account set that i need to enter when ubuntu load's, but i had no choice in this when  installing - can i get rid of this so i no longer need to enter a name and password? i thoght about deleteing the account from user accounts but im not sure if that will make it load without it? or i will be locked out

thanks

---

### Post by taurus on 2007-03-06
If you don't have an account, you can't log in.  That's the way Unix/Linux works.  And if you don't feel like login in each time you boot Ubuntu, then you can go with the auto login which means the machine will boot and log you in automatically.

---

### Post by jamienos on 2007-03-06
> **taurus said:**
> If you don't have an account, you can't log in.  That's the way Unix/Linux works.  And if you don't feel like login in each time you boot Ubuntu, then you can go with the auto login which means the machine will boot and log you in automatically.

How would i go about setting it to auto login with it?

---

### Post by aysiu on 2007-03-06
> **jamienos said:**
> How would i go about setting it to auto login with it?
It depends. Are you using Ubuntu, Kubuntu, or Xubuntu?

---

### Post by jamienos on 2007-03-06
> **aysiu said:**
> It depends. Are you using Ubuntu, Kubuntu, or Xubuntu?

Ubuntu.

---

### Post by konst88 on 2007-03-06
Alt+F2
gksu gdmsetup
Security
Tick automatic login

---

### Post by aysiu on 2007-03-06
> **jamienos said:**
> Ubuntu.
Go to System > Administration > Login Window > Security, and there should be an option to log in automatically.

---

### Post by jamienos on 2007-03-06
> **aysiu said:**
> Go to System > Administration > Login Window > Security, and there should be an option to log in automatically.

Perfect! thankyou.

---

