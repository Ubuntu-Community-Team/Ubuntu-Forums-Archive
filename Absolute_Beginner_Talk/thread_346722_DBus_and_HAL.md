---
title: "DBus and HAL"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-01-26
Hi everyone, everytime I turn my comp on it gives me this "Failed to initialize" HAL error. I can't access any administrative features or my SDCard. The only way I can sort it out is by typing in the terminal "sudo aptitude reinstall dbus". Everything works after I log out and back in but not when I restart my computer.

I uninstalled dbus a long time ago but now it is reinstalled, what do you think the problem is? Thanks. :guitar:

---

### Post by citizenofnowhere on 2007-01-26
Hi!

Check that dbus is set to launch on startup (System->Administration->Services).

Also, try reading this thread:

[https://launchpad.net/ubuntu/+source/hal/+bug/24029](https://launchpad.net/ubuntu/+source/hal/+bug/24029)

If you look in the comments section, there's a few about debugging the problem. There is a command to help you test if dbus is running when you first start-up your machine.

In this thread you will also find a link to another thread. In the second thread, comment #16 has a fix for the bug (assuming it's the same).

Hope that helps!

---

### Post by Bagboy23 on 2007-01-27
Done! The services thing worked. Thanks mate.

---

### Post by citizenofnowhere on 2007-01-27
yay! :)

---

