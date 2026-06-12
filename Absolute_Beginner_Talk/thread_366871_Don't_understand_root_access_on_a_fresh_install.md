---
title: "Don't understand root access on a fresh install"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by CaptSaltyJack on 2007-02-21
On a fresh install of Ubuntu, when I perform admin tasks like Synaptic, it asks for admin password.. I enter the password for my own personal account which works.  But in bash, if I do "su", the password won't work there.  So what exactly is the root password, because the install process never asks me to set that.  I assume Synaptic and other GUI root apps work because my user account is in the 'admin' group.

---

### Post by Maestro23 on 2007-02-21
RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by CaptSaltyJack on 2007-02-21
Ahhh, sudo -i.  I was wondering how to open a root shell.  Too late. :)  I already did "sudo passwd root" and changed root password to something I can get into using "su".
No biggie, was just wondering in case I'm helping a Linux n00b set up Ubuntu.  They probably won't be messing with shell much anyway, though.

---

### Post by macogw on 2007-02-21
CaptSaltyJack, it's suggested that you not tell other newbies about setting a root password.  The password is by default some random jumble of god-knows-what to make it harder for a password-cracker to get in.  Your personal password is easier to crack (probably) but it would require them knowing your username as well.

sudo -i?  I always use sudo -s for that.

---

### Post by Bachstelze on 2007-02-21
sudo -i is recommended over sudo -s, man sudo will explain why better than me :p

---

### Post by macogw on 2007-02-21
er...yeah...i dont get it.  reading man sudo is how i found -s, but i dont really get what the difference is.  is it like the difference between "su" and "su -"?

---

