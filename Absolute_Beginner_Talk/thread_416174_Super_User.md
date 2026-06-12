---
title: "Super User ?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by NovaNine on 2007-04-20
Hi again guys !

I downloaded the "ati-driver-installer-8.35.5-x86.x86_64.run" and now when i want to install it, it tells me that i can only install in super user mode ...
What's that ? And how do you get in this mode ?

Thanks !

---

### Post by taurus on 2007-04-20
```
sudo ./ati-driver-installer-8.35.5-x86.x86_64.run
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by eentonig on 2007-04-20
It's the 'Administrator' mode.

You can't get in that mode (by default), but you can run programs as root (administrator). Just use the word "sudo" in front of the command you want to run as admin.

---

### Post by z1p101 on 2007-04-20
New question

I'm looking to switch to Ubuntu and I'm wondering, is there a root account? Or are there just sudo users and permissions?

---

### Post by bobplano on 2007-04-20
there is a root account but it is not recommended to unlock it

---

### Post by %hMa@?b&lt;C on 2007-04-20
it is possible to set up a normal root account, but the entire distro is based on sudo and permissions.

---

### Post by taurus on 2007-04-20
Yes, you can unlock root account but be real _careful_ with it.

```
sudo passwd root
```

**Disclaimer**:  I will NOT take responsibility if you screw up your machine when you log in as root.

---

### Post by NovaNine on 2007-04-20
OK. Thanks all for your help :D

---

### Post by z1p101 on 2007-04-20
One more question
My knowledge is with Gentoo BSD Fedora in that order.
Is the OS permissions set up as
root =Don't touch it unless you know exactly what you are doing.
sudo=What root does most of the time, ex. install new software.
everyone else=You are not allowed to clobber my system.

And where is the line drawn, or is it something else?

---

