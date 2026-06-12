---
title: "Virtual Box Error"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by munch3 on 2008-03-26
> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
this shows up...

---

### Post by kpkeerthi on 2008-03-26
You need to be member of vboxusers group
```
sudo gpasswd -a <your-user-id> vboxusers
```

Logout and log back in.

---

### Post by munch3 on 2008-03-26
I am

---

### Post by kpkeerthi on 2008-03-26
> **munch3 said:**
> I am

Can you post the output of 
```
groups
```
command from a terminal?

---

### Post by munch3 on 2008-03-26
works now, had to reboot

---

### Post by munch3 on 2008-03-26
ty btw

---

