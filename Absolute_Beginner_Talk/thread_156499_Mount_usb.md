---
title: "Mount usb?"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by gambithunt on 2006-04-07
Hi all

I'm brand spanking new at linux and have just installed Ubuntu on a Dell optiplex GX520 and gnome cannot start up becasue of the vid-card.

I have downloaded the drivers from intel and have added them onto a usb, how can I mount my usb?

Also does does anyone know the password for the root account by default?

Your help would be much appriciated.

-G

---

### Post by frodon on 2006-04-07
The basic mount command is : ```
sudo mount /dev/*device_name* *The_directory_where_you_want_to_mount_the_device*
```
For root things, you should read that : [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by akudewan on 2006-04-07
It will look something like ```
 sudo mount /dev/sda1 /mnt/usb/ 
```

make sure you have created the /mnt/usb directory first

---

### Post by Wyrm_1972 on 2006-04-07
When I first installed Ubuntu I too had to mess to get Gnome to start, but all it was was Ubuntu trying to boot up into too high a res mode.

Have you looked at this? [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Too see if it helps?

---

