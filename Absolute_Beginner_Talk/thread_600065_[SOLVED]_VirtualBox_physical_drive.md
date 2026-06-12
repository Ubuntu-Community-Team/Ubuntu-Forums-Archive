---
title: "[SOLVED] VirtualBox physical drive"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-11-01
Hello,

I sthere a simple way to use my physical partition (windows XP) with Virtual Box? I read the manual but I have no idea on how to do it.

I also encountered this problem during the install of the virtual machine:

> The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

It was solved when I added my user to virtualBox group in System > Administration > Users and Groups.

---

### Post by Arthur Archnix on 2007-11-01
Is that a question, a statement, or a reply to another thread?

---

### Post by the8thstar on 2007-11-02
Sorry, I corrected my previous post. Thanks for letting me know about it!

---

### Post by the8thstar on 2007-11-08
Bump

---

### Post by the8thstar on 2007-11-11
Ok, I found it in Chapter 9.9 of the VirtualBox helpfile.

---

