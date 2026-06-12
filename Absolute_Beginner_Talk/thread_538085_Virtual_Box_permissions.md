---
title: "Virtual Box permissions?"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Fonon on 2007-08-29
As I try to boot up a VM of React OS so I can see if I like it or not, I get this error message:

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

I have no idea how to add write permissions.  Can someone please help me?

---

### Post by schorsch on 2007-08-29
Type:
```
sudo usermod -aG vboxusers *your_user_name*
``` in a terminal and change *your_user_name* to your_user_name (just a guess: fonon?).
Logout, login again and you should be done.

---

### Post by kellemes on 2007-08-29
Using the gnome-usermanager you can add the user to vboxusers.
Don't use gnome myself but it's somewhere in the administration menu.
Logout -> login.

Edit: sorry for the duplicate.

---

### Post by Fonon on 2007-08-29
> **schorsch said:**
> Type:
```
sudo usermod -aG vboxusers *your_user_name*
``` in a terminal and change *your_user_name* to your_user_name (just a guess: fonon?).
Logout, login again and you should be done.

Nah, my user name is my real name.  I put the stuff into the terminal, and I suppose it went smoothly, cause it didn't give me any feedback.  Once this package is done downloading, I'll log out and let ya know how it went.

---

