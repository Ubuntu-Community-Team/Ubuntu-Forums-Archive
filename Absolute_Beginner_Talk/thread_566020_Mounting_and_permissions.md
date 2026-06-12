---
title: "Mounting and permissions"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by aepyx on 2007-10-02
I really don't have a problem mounting devices but when I mount a drive or a network drive to a folder the owner and group permissions change to root, why is that?  Is there a method to change the permissions back.  Using the a standard chmod or chgrp doesn't change the permissions on the mounted folder.  Not sure what to do about it.  I can connect and see files but I can't write to the folder or change the permissions on the folder.

More specifically I am mounting to a smbfs on another computer that is running ubuntu.

```
sudo mount -t smbfs //workgroup/share /media/share share -o username=myusername,ip=192.168.1.10
```

This permission thing also happens with things like a removable harddrive.

-Dan

---

### Post by aepyx on 2007-10-03
helloooooooo, i feel so alone :(

it's getting late, i'll check back tomorrow.

---

### Post by cvaty on 2007-10-03
how about the same command, without the sudo

---

### Post by apostate on 2007-10-03
By putting in SUDO, you are invoking root privileges to do this command, so it ends up "getting done by root"...if that makes sense?

Of course, you have to do this or it won't work, which is a bit off-putting to a new person. So try:

sudo chown [username] folder

Which is using root privileges to change ownership of the folder, drive, share, etc. to you.

---

### Post by K.Mandla on 2007-10-03
You might be able to get around that by adding the mount location to your fstab, and giving user-level permissions to mount it. For example, on my USB thumb drive which is ID'd as /dev/sda1 ...

```
/dev/sda1 /media/usbdisk vfat users,noauto 0 1
```
*/media/usbdisk* is the mount destination, *vfat* is the filesystem, *users* gives mount permission to users, and *noauto* tells Linux not to mount it automatically. 

Now I can 

```
mount /dev/sda1
```
and it's automatically dropped into place. (As a side note, I make a symlink in my home directory to /media/usbdisk with *ln -s /media/usbdisk ~/usbdisk* ...)

The only downside is if the drive is mounted with a different identifier, then it doesn't quite work. I usually add sda1 and sda2 to my fstab, just to cover the bases.

There's more in *[man mount]("http://www.die.net/doc/linux/man/man8/mount.8.html")*. (There's a better explanation [here]("http://kmandla.wordpress.com/2007/03/08/howto-mounting-without-sudo/"), along with a bash script that will mount or unmount the drive automatically. It's great for Openbox systems. :) )

---

### Post by aepyx on 2007-10-04
I am going to try all the ideas when I get home in about an hour.

Thank you for all the help!

-Dan

---

