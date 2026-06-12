---
title: "Root password"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by redo109 on 2006-06-26
Hi I installed Ubuntu 6.06 last night but was out during the last half of install and was never prompted for a root password when I try to use something like apt-get after I type sudu  I'm asked for a password but I didn't set one, is there a default one.
Thanks
Richard

---

### Post by DCM36 on 2006-06-26
[QUOTE=redo109]Hi I installed Ubuntu 6.06 last night but was out during the last half of install and was never prompted for a root password when I try to use something like apt-get after I type sudu  I'm asked for a password but I didn't set one, is there a default one.
Thanks
Richard[/QUOTE]

Ubuntu is set up not to use the root account at all, and sets a random password at install for it. When you use sudo, enter the password for your user account when it prompts you. If you do some googling, you can figure out how to change the root account's password and enable logging in with it. Or if get tired of constantly using sudo, you can either use "sudo -s" or use the Alacarte Menu Editor to enable the root console in System Tools.

---

### Post by aysiu on 2006-06-26
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by redo109 on 2006-06-26
Many thanks to you both I understand now. I'm very pleased with the install and the amount of help online.
Thanks
Richard

---

