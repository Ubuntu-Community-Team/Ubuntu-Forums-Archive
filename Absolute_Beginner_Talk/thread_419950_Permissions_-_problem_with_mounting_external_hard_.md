---
title: "Permissions - problem with mounting external hard drive"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by pilllango on 2007-04-23
Hi folks, 

I have a problem with mounting my external usb ntfs hard disk: I can access it only with root privileges, no matter if I changed the permissions/ownership of the mount-point: 

After mounting it as "user" the permissions/ownership automatically changes back to "only root stuff", letting me  only mount-unmount it as user without any access. Here is my fstab-line referring to it, 'guess no problem with it:

         /dev/sdb1 /media/Shoop          ntfs          user,noauto,ro,exec        0         0

Can somebody tell me what is going on?

Thanx in advance!

---

### Post by goldaryn on 2007-04-23
This may help:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

---

### Post by pilllango on 2007-04-23
Thank you! It helped me a lot, I edited the fstab with

/dev/sdb1    /media/Shoop    ntfs    noauto,nls=utf8,umask=0222,user    0    0

and now it works!  Apparently the "umask" option was the key.

---

### Post by goldaryn on 2007-11-26
You're welcome! ^ ^

---

### Post by MrKlean on 2007-11-26
I have the same problem..but when I add this line

/dev/sdc1 /media/My Book ntfs noauto,nls=utf8,umask=0222,user 0 0

it tells me the line is bad ; (  it's VERY frustrating LOL!!
thanks !!

---

### Post by qpieus on 2007-11-26
You're getting an error because of the space in "My Book". 
Try this in your fstab line
```
/dev/sdc1 /media/My\ Book ntfs noauto,nls=utf8,umask=0222,user 0 0
```

The backslash after "My" should tell the system to ignore the space. Hopefully this'll work (I haven't had to use a backslash in fstab - all my mount points have no spaces).

---

### Post by MrKlean on 2007-11-26
Thanks ; )  I'll give it a try ; )

---

### Post by MrKlean on 2007-11-26
nope...still says line is bad..and I double checked the dev no. and mount point ; )  I'm using ntfs-3g.  If that matters at all.  I can run gnome commander and it works with sudo...just can't mount it without it ; (  Grrrrr

LOL!!

---

### Post by MrKlean on 2007-11-26
push.. ughhhhhh   ; )

---

### Post by qpieus on 2007-11-27
In the fstab line, try changing the mount point to /media/mybook (no spaces). You may need to create this directory ahead of time (not sure about that - usually the /media directory is used for automounting usb devices and the user usually doesn't create directories there).

Another option would be to change the mount point to someplace in your /home directory. This way you should have the proper permissions and you wouldn't be messing around with the /media directory. Again, make sure there are no spaces in the mount point.

One other thing, before ntfs-3g support was incorporated into ubuntu (we have to install it separately), the fstab line for an ntfs device had "ntfs-3g" instead of "ntfs". Since ntfs-3g support comes standard with ubuntu now, maybe that's not needed anymore and just plain ntfs is OK. You could try that though.

---

