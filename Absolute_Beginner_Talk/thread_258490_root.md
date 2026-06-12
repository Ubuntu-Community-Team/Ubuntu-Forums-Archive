---
title: "root"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2006-09-16
everytime I tpye dpkg --configure, it tells me I need "superUser" rermissions or something like that.  I've only set up one account but how do you set up/log into the super user account?:)

---

### Post by bodhi.zazen on 2006-09-16
use sudo

ie```
sudo dpkg --configure
```

enter your user (log in) passwrod when asked (you will not see text on the screen as you type).

---

### Post by Klaidas on 2006-09-16
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aktiwers on 2006-09-16
Or

```
sudo su
```

---

### Post by mixmaster on 2006-09-16
sudo -i will give an interactive root session.  Generally it is better to use 
sudo <command>
for each separate command as it prevents the possibility of leaving a session around with root permissions and doing something dire by mistake later.

---

