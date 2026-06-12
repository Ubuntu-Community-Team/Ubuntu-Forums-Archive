---
title: "how to set dafault OS in grub?"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by binilbenjamin on 2006-04-10
I have a dual boot system with ubuntu & winxp!! but the grub is set to boot ubuntu by default.How can i change that to windows??And how can i reduce the waiting time??

---

### Post by ubernoob on 2006-04-10
sudo gedit /boot/grub/menu.lst

check for "default" and "timeout"

---

### Post by sYs^ on 2006-04-10
Hi, you will have to edit the /boot/grub/menu.lst file:

**timeout**		10 
This is the "waiting time", default: 10 sec

And here's a howto about changing the default OS:
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

