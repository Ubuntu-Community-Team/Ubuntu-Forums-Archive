---
title: "virtualbox settings"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by deepblue80 on 2007-08-26
hi
i am trying to install virtualbox on Ubuntu 7.04. the install ran smoothly, and i started virtualbox and clicked on new and named it windows as i intend to run windows xp sp2. now i allocated 750 mb ram, 20gb fixed hdd. then i started the windows virtualbox for the first time by clicking in the list on the left hand side.
Then the first time setup wizard took a few details which i have attached as a screen shot 1. then i click finish and it gives me an error which is attached as  screen shot 2.
i reproduce the text here to help - 

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

any ideas on how to add users as required above?

---

### Post by schorsch on 2007-08-26
Either

System --> Administration --> Users and Groups --> Manage Groups

then choose the group "vboxusers" and add your user to this group

or

```
gksudo gedit /etc/group
```
and add your users to line startting with "vboxusers" at the end.

Login, logout and you should have fixed this problem.

---

