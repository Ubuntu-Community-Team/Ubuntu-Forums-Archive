---
title: "[SOLVED] help with virtualbox"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-12-10
I get this error when trying to install from a cd:
> 

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



what now?

---

### Post by overdrank on 2007-12-10
> **staticvoid said:**
> I get this error when trying to install from a cd:


what now?

HI you can
go to systems>administration>users and groups
select manage groups,look for the group VBOXUSERS,
select properties and check the box in front of your user name.
Or use this command
```
sudo adduser username vboxusers
```
or
```
chmod 660 /dev/vboxdrv
```
And always the user manual
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by staticvoid on 2007-12-10
Thanks,

I'll try it soon. I set the permissions- a little different in kubuntu- and will try installing debian soon with VirtualBox, Can't wait to test out distros!!  :D

sv

---

### Post by schorsch on 2007-12-10
> **overdrank said:**
> 
```
sudo adduser schorsch vboxusers
```
... ermmm ... you should use YOUR username and not mine .... ;-)

and if you want to add an already existing user to another group you should try

```
usermod -aG vboxusers *your_user_name*
```
because otherwise the permissions of the existing user to use sudo will perhaps be deleted.

---

### Post by overdrank on 2007-12-10
> **schorsch said:**
> ... ermmm ... you should use YOUR username and not mine .... ;-)

and if you want to add an already existing user to another group you should try

```
usermod -aG vboxusers *your_user_name*
```
because otherwise the permissions of the existing user to use sudo will perhaps be deleted.

Sorry my apologizes, I must have copied and paste and not removed. :oops:

---

### Post by staticvoid on 2007-12-11
Hahaha..

Thanks you guys. I got it working. And actually I did not open a terminal even once. I just did it with the GUI :). But those commands are helpful. Especially
usermod -aG vboxusers your_user_name

ok, I'm out. Thanks again!!

---

