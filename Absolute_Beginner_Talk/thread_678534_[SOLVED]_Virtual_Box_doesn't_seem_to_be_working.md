---
title: "[SOLVED] Virtual Box doesn't seem to be working"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by NovaAesa on 2008-01-26
I'm wanting to install another OS using Virtual Box, but it isn't working for me. I got the following error:

> The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I'm still a bit new with Linux, and am not really sure what this message is telling me to do. Can someone help me to get it working?

---

### Post by overdrank on 2008-01-26
> **NovaAesa said:**
> I'm wanting to install another OS using Virtual Box, but it isn't working for me. I got the following error:


I'm still a bit new with Linux, and am not really sure what this message is telling me to do. Can someone help me to get it working?

HI you can try
go to systems>administration>users and groups
type your administrator password
select manage groups,look for the group VBOXUSERS,
select properties and check the box in front of your user name
or
```
chmod 660 /dev/vboxdrv
```
And always the user manual
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by NovaAesa on 2008-01-26
Thanks!! That got it to work. xD

---

