---
title: "virtualbox how to?"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by robalcorn on 2008-03-15
When I try to install a o/s under virtualbox I get this message :


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 I went to system/administration/users and groups but don't see an option to allow me to have permissions am I looking at the wrong place?

---

### Post by bumanie on 2008-03-15
Follow this guide and you should get everything sorted.
[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

---

### Post by robalcorn on 2008-03-15
Thanks that did the job and also have usb support

---

