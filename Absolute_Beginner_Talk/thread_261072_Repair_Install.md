---
title: "Repair Install?"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by rubikfreak on 2006-09-19
I modified my repositories (/etc/apt/sources.list) and I replaced each "dapper" with "edgy" in an attempt to upgrade my installation to Edgy Eft Knot 3. Upon reboot, the X Server came up with the message similar to "X Server not configured properly". Is there any way that I can configure X Server properly or even better, perform a complete reinstall without harming the files in my /home/ and/or Desktop folder?

---

### Post by jimrz on 2006-09-19
> **rubikfreak said:**
> I modified my repositories (/etc/apt/sources.list) and I replaced each "dapper" with "edgy" in an attempt to upgrade my installation to Edgy Eft Knot 3. Upon reboot, the X Server came up with the message similar to "X Server not configured properly". Is there any way that I can configure X Server properly or even better, perform a complete reinstall without harming the files in my /home/ and/or Desktop folder?

In the terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by gratuit on 2006-09-21
Also, if you keep your /home as a seperate partition, I've found you can do a complete re-install, create users with the same names as your old ones, and just delete the home directories created by the install, then mount your home partition and update fstab accordingly. if you keep your skins, icons, etc in your home directory, different installs can seem almost transparent. (you might have to chown the directories and files ymmv)

---

### Post by rubikfreak on 2006-09-23
Thanks, guys. I created a seperate parition, then reinstall dapper 6.06.1. I then copied the old home folder over to the new install, deleted the old partition, and resized the new partition using the GParted livecd to take up the whole drive. I like the idea for having the home folder on a seperate partition, though.

---

