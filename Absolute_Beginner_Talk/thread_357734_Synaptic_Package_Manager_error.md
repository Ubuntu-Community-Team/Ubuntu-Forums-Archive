---
title: "Synaptic Package Manager error"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-02-10
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

When I run dpkg --configure -a it says I need to says requested operation requires superuser privilege

And now I can't install my updates.:confused:

---

### Post by tonyr1988 on 2007-02-10
Applications -> Accessories -> Terminal

> sudo dpkg --configure -a

Enter your user password when prompted.

---

### Post by Maestro23 on 2007-02-10
> **Repent said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

When I run dpkg --configure -a it says I need to says requested operation requires superuser privilege

And now I can't install my updates.:confused:

sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

#sudo dpkg --configure -a

---

### Post by Repent on 2007-02-10
Thank You.\\:D/

---

### Post by tonyr1988 on 2007-02-10
If you get a chance, read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It'll give you some background information on sudo (kind of a "temporary superuser") ("superuser" = "administrator" = "root")

---

