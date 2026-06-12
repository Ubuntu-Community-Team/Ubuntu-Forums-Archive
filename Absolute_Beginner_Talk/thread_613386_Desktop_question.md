---
title: "Desktop question"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Scott-271 on 2007-11-14
I'm kinda new to Ubuntu, so please bear with me. :-D

I just installed Ubuntu 7.10 minimal and xfce, and pretty much only the apps I wanted; on a multi-boot system. I've been using xfce for over a year now on another distro, and actually found Xubuntu kinda heavy - hence the minimal unstall.

My question is, I now have all the *volumes* from the other os's on my desktop. I want to make them go away, without losing home, file system, etc. Not completely, just off my desktop; still showing up on the places applet would be fine or somewhere else accessible. As well as possibly adding desktop icons of other apps. 

How can I go about this? Preferably without the need of a hammer and/or a lot of beer.:lol:

Thanks in advance,
Scott

---

### Post by taurus on 2007-11-14
You mean you want to mount those partitions somewhere else besides /media.  Well, you can mount them to /mnt if you wish so you need to edit /etc/fstab.

```
gksudo mousepad /etc/fstab
```
Once you change the mountpoints, don't forget to create the new ones or they won't get mounted.

```
sudo mkdir /mnt/first_mount_point  /mnt/second_mount_point  /mnt/third_mount_point
```

---

### Post by Scott-271 on 2007-11-14
Ok, now is /first_mount_point ,etc, is that sda1 or whatever; or is it 23G volume?

---

### Post by taurus on 2007-11-14
sda1.  For instead, if you want to mount /dev/sda1 to /mnt/sda1 in /etc/fstab, then you need to create a mount point, /mnt/sda1, for it.

```
sudo mkdir /mnt/sda1
```

---

### Post by Scott-271 on 2007-11-14
Ok thanks.

I just did that with two volumes, that I wasn't too concerned about losing. Nothing happened. Do I need to reboot to see the changes?

---

### Post by Inxsible on 2007-11-14
simply do a ```
sudo mount -a
``` that should re mount all of the drives again. The ones that you changed over to under /mnt will not come up on your desktop

---

### Post by Scott-271 on 2007-11-14
Had to reboot, but it all worked. 

Thanks a lot! :D

---

### Post by Dr Small on 2007-11-14
Please remember to mark your threads as Solved from Thread Tools. ;)
Thanks :D

---

