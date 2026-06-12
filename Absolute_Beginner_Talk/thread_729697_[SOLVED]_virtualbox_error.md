---
title: "[SOLVED] virtualbox error?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2008-03-20
what does this mean and what does it want me to do? and then also how do i do it :)

"The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE)."

thanks in advance

---

### Post by Captainm on 2008-03-20
You need to add your user to the vboxusers group. In a terminal type (without the brackets):

```
sudo usermod -G vboxusers -a [your username]
```

Reboot and it should work.

---

### Post by kamitsukai on 2008-03-20
Thanks

---

