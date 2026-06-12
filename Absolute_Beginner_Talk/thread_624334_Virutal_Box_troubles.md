---
title: "Virutal Box troubles"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by vsugadhan on 2007-11-26
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


This is what it says when I try to create an Xp system. I know this is somethng basic and had noticed the VirtualBox telling me to do the same thing during installation. The thing is I have no idea how to make the permissions correct. Any help?

---

### Post by overdrank on 2007-11-26
> **vsugadhan said:**
> The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


This is what it says when I try to create an Xp system. I know this is somethng basic and had noticed the VirtualBox telling me to do the same thing during installation. The thing is I have no idea how to make the permissions correct. Any help?
HI you can
go to systems>administration>users and groups
type your administrator password
select manage groups,look for the group VBOXUSERS,
select properties and check the box in front of your user name.
Or use this command
```
sudo adduser schorsch vboxusers
```
or
```
chmod 660 /dev/vboxdrv
```
And always the user manual
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by spiderbatdad on 2007-11-26
maybe open a terminal and type:

```
ls -l /dev/vboxdrv
```

take note of the existing permissions.

permission are rwx   read, write, execute. for the following, in order: user, group, others.
to make a change to allow users write permission you would ensure the first set of permissions includes a "w"

```
sudo chmod -rwxr-xrwx
```
gives user  read, write, execute permission. group has read, execute permission, and others have read, write, execute permission. The dash in front of the first set of permissions means it is a file. If you see a "d" in front of the first set of permissions, it is a directory.

you can:
```
ls -l /home/yourusername
```
to look at all the permissions set for files and directories in your home folder. Do ls -al /home/you and it will includes hidden files.

---

