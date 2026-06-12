---
title: "Virtual Box Help Please"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Tootles on 2007-09-15
Get this error after i try and run an os in virtual box

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by Sayers on 2007-09-15
Firstly read the error. Now that you understand it

sudo adduser vboxusers [yourusername]

---

### Post by Tootles on 2007-09-15
sergey@sergey-desktop:~$ sudo adduser vboxusers Sergey
adduser: The user `vboxusers' does not exist.
sergey@sergey-desktop:~$ sudo adduser vboxusers [Sergey]
adduser: The user `vboxusers' does not exist.
sergey@sergey-desktop:~$

---

### Post by Harpoon on 2007-09-16
Ok, try using the CUI:  System >> Users and Groups, and see if that works for you.

---

### Post by asmoore82 on 2007-09-16
I wanted to kill 2 birds with one stone ...

1. I wanted the Vbox kernel module loaded on every linux boot.
2. I wanted wanted the permissions good to go; which I defined as being accessible to users in the "admin" group ...

so I created a new text file "/etc/modprobe.d/virtualbox" ... you could do so with the command

```
~$ gksudo gedit /etc/modprobe.d/virtualbox
```

and the contents of that file should be
```
alias virtualbox vboxdrv

install vboxdrv /sbin/modprobe --ignore-install vboxdrv && \
        { chown 0:admin /dev/vboxdrv ; }

#End of File
```

after placing the file there, the module will be loaded on every boot;
however you will need to load it and change the ownership the first time by hand
if you don't wanna reboot ...

```
~$ sudo modprobe virtualbox
~$ sudo chown 0:admin /dev/vboxdrv
```

P.S. no birds or animals of any kind were harmed.

---

### Post by everdred on 2008-04-08
> **Tootles said:**
> sergey@sergey-desktop:~$ sudo adduser vboxusers Sergey
adduser: The user `vboxusers' does not exist.
sergey@sergey-desktop:~$ sudo adduser vboxusers [Sergey]
adduser: The user `vboxusers' does not exist.
sergey@sergey-desktop:~$

Actually, reverse your username and group name.

For instance, I'd use:

sudo adduser everett vboxusers

---

