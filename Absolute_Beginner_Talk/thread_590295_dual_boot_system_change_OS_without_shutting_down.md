---
title: "dual boot system: change OS without shutting down?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by sagesparrow on 2007-10-24
In dual boot setup, can you change between operating systems without shutting down?  if so (and i think there must be an easy way) how to go from XP to GRUB (then select Ubuntu) and how to get directly to GRUB  from Ubuntu?
thanks

---

### Post by qamelian on 2007-10-24
Nope, that's why is called dual boot instead of dual OS. To do what you appear to want to do, you would need to use virtualization (vmware, virtualbox, etc) to run one OS inside another.

---

### Post by jrharvey on 2007-10-24
Using an emulator such as virtualbox works great for me. I hate having to restart the computer. Virtualbox is very fast and can run on 64 bit OS. It is a very cool program.

---

### Post by jrharvey on 2007-10-24
You can't do this because an OS basically tells your computer what to do and how to run. If you had 2 then your computer would be very confused. ;)

---

### Post by paOolkim on 2007-10-24
hey, i just installed vritualbox , and i setup a windows xp as my virtual pc.
then i tried to start it and got this error message.


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
can you provide easy enough directions that a child can do it?

---

### Post by sagesparrow on 2007-10-24
Thanks for the info.  would there be any problems associated with keeping a dual boot setup (xp/ubuntu) AND using some virtualization (vmware, etc.) for xp?  I'm just trying things out to see what will work for me over time.

---

