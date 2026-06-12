---
title: "Where do I get/how do I install VMWare"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-11-08
Can I use the Synopitic to get it?

---

### Post by Dapman01 on 2007-11-08
Never Mind, I decided to use virtualbox

---

### Post by ubnewbie2 on 2007-11-08
> **Dapman01 said:**
> Can I use the Synopitic to get it?

Yes, it is packaged.

If that doesn't work, you can download it from vmware themselves and follow the instructions on running the installation scripts.

---

### Post by Dapman01 on 2007-11-08
Can someone tell me how to use Virtualbox

---

### Post by Maestro23 on 2007-11-08
> **Dapman01 said:**
> Can someone tell me how to use Virtualbox

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Give the documentation a read, get into trouble... post your questions.

*There's a ton of threads on the boards for setting up VB as well.

---

### Post by Dapman01 on 2007-11-08
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 That is what I get when I start up the Virtual Machine
I never used my Vista disk yet so I don't know what is going on

---

### Post by ubnewbie2 on 2007-11-08
So, did you add yourself to thevboxusers group as it says?

---

### Post by Dapman01 on 2007-11-08
where did it say that

---

### Post by Maestro23 on 2007-11-08
> **Dapman01 said:**
> where did it say that

First line.

Do:

System > Administration > Users and Groups

Add the user to the vboxusers group.

---

### Post by ubnewbie2 on 2007-11-09
That will fix it - I just did it myself

---

