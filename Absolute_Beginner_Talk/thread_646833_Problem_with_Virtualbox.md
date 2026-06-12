---
title: "Problem with Virtualbox"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by hockeyfighter09 on 2007-12-21
I just installed virtualbox through synaptics and whenever I try to boot up fedora in it or any other linux distro I get this message. 



The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 


What do I do?

---

### Post by heatpumpcontrol on 2007-12-21
> **hockeyfighter09 said:**
> I just installed virtualbox through synaptics and whenever I try to boot up fedora in it or any other linux distro I get this message. 



The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 


What do I do?

In the Manual it tells you that you must be a member of Virtualbox users in order to run it.
System --> Administration --> Users and Groups -->Manage Groups -->vboxusers and double click. Add yourself (place check next to your name) and try it again.

---

### Post by hockeyfighter09 on 2007-12-21
Thanks alot for the reply. This fixed my problem I can now run things in it. Thanks alot!:)

---

