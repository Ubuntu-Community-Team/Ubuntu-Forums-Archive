---
title: "get an error when tryn to start virtual machine"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Nedux on 2007-10-25
hi there ` , i get a strange error when i try to start virtual machine `, 
I followed exactly this steps here `, to instal and setup new virtual machine ,
[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

Please help `., here is the error


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

---

### Post by schorsch on 2007-10-25
Just add your user to the group "vboxusers"as mentioned, reboot and the error will be gone.

---

### Post by Nedux on 2007-10-25
now I get this error `, 


Unknown error creating VM (VERR_HOSTIF_INIT_FAILED).
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by Nedux on 2007-10-25
still need help here `, i realy need to have this working

---

### Post by schorsch on 2007-10-26
Are you using bridging for your network interface? Then I would try NAT first; this works on my installation very well. Please also take a look [here]("http://ubuntuforums.org/showthread.php?t=464199").

---

### Post by ronmarley1 on 2007-10-26
> **schorsch said:**
> Just add your user to the group "vboxusers"as mentioned, reboot and the error will be gone.

Just a side note here...  You do not need to reboot after adding yourself to the group.  Logout/login is fine.
Sorry I do not have a solution for your error.

---

