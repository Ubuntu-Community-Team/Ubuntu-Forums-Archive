---
title: "super user problems"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by callum_G on 2007-01-29
how do i login in to super user to install the ati video driver?

---

### Post by jordanmthomas on 2007-01-29
either use 
```
sudo command
```
to run one command with root privileges or type 
```
sudo su
```
to get a root shell.  When you are done, type exit to quit

Read more here:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by callum_G on 2007-01-29
it starts to expand the file then says again "you must be super user to run this installer"

---

### Post by jordanmthomas on 2007-01-29
what command did you type to run the installer?
You should have put sudo in front of it.

as in:
```
sudo ./installername
```

---

### Post by Norfolk 'n' Good on 2007-01-29
```

sudo -s

```

---

### Post by antiwindows798 on 2007-01-29
Running as root will solve the problem too (I think).

---

