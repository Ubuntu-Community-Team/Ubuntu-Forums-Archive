---
title: "Gow to find forgotten password?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Sinergy on 2007-05-16
My previous install of ubuntu was installed ahwile ago, i know my username, but i do not know my password, im not really sure about all the linux lingo yet, so if someone could give me a very simple lamens term set of instructions on finding my password that would be great.

---

### Post by aysiu on 2007-05-16
You can't really find it, but you can easily reset it.

Boot into recovery mode (the option right below the one you usually boot to), then type ```
passwd sinergy
reboot
```

---

### Post by taurus on 2007-05-16
Boot into recovery mode from GRUB menu and at the prompt, change your password. 

```
passwd **john**
```
Assuming **john** is your login name.  Then, reboot and see if you can log in with your username and the new password.

```
shutdown -r now
```

---

