---
title: "Check on locked root"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by dwiedenfeld on 2007-10-03
I understand that in Ubuntu, the root user account is "locked", and normally to make changes one has to use sudo or gksudo. I also understand that it is possible for it to be unlocked.

The question is, how can I tell if the root user account is locked or if it has been unlocked?

---

### Post by taurus on 2007-10-03
```
ls -la /root
```

---

### Post by bodhi.zazen on 2007-10-03
sudo cat /etc/shadow | grep root

The second field is the password field and should have a ! in it.

if it has a !<string of letters/numbers> it has been set and is now locked, like this :

root:**!**$1$fi9qrEEl$RXc1Fy0hEVaCCWQilxyz:13789:0:99999:7:::

Note the !

---

### Post by master_kernel on 2007-10-03
I think if you run
```
sudo passwd root
```
you can set the password and 'unlock' it.

---

### Post by psusi on 2007-10-03
The root account is not locked in Ubuntu.  By default it has no password, but is not allowed to login to the gui.  Switch to a tty and you can login as root.

---

### Post by bodhi.zazen on 2007-10-03
> **psusi said:**
> The root account is not locked in Ubuntu.  By default it has no password, but is not allowed to login to the gui.  Switch to a tty and you can login as root.

> **By default, the root account password is locked in Ubuntu.**

*direct quote, bold text and all, from [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

