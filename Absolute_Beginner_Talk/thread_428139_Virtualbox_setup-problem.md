---
title: "Virtualbox setup-problem"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by unixdotseth on 2007-04-30
After installing Virtualbox and trying to boot up my virual machine i get this error what do i do?




VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect.
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by useResa on 2007-04-30
In order to be able to use VirtualBox you must add yourself to the vboxusers group.
This can be done as follows:
Open **System --> Administration --> Users and Groups**
Click **Manage Groups**
Look up the *vboxusers* group in the list, select it and click **Properties**
In the users list find yourself and mark yourself.
Click **OK**, close any left open windows _and reboot_.

This should solve your issue. Good luck.

---

### Post by compiledkernel on 2007-04-30
Well read UseResa. 

to the OP, this thread is a good read over for Virtualbox. 

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

---

### Post by useResa on 2007-04-30
> **compiledkernel said:**
> Well read UseResa. 

to the OP, this thread is a good read over for Virtualbox. 

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)
Thank you for this link, I did not have this one yet  ;)

---

### Post by compiledkernel on 2007-04-30
Eh. Bodhi.zazen is the virtualbox master.

---

### Post by scotttkd on 2007-05-01
that link has completely sold me on virtualbox.  It was exactly what is needed to integrate the program into the host.  many thanks!!

---

