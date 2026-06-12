---
title: "VirtualBox problems"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by moondoggy17 on 2008-02-18
thow do i fix this
> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

---

### Post by JoshuaRL on 2008-02-18
Okay, go to System->Administration->Users and see if you can add that permission to the user you're in right now.  You are using a Super-User capable of using sudo right?

---

### Post by raydeen on 2008-02-18
[http://ubuntuforums.org/showthread.php?t=612284](http://ubuntuforums.org/showthread.php?t=612284)

---

### Post by wolfen69 on 2008-02-18
System --> Administration --> Users and Groups, click Manage Groups, scroll down to vboxusers, click on it then click properties, then click the checkmark next to your user name. Click OK, close the User window, then run Virtualbox.

---

