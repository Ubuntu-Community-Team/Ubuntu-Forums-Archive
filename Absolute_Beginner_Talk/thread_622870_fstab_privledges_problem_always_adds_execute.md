---
title: "fstab privledges problem: always adds execute"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-11-25
I am not using gnome, so to facilitate mounting usb drives, I added a line in the fstab file:

```
/dev/sda1       /media/usb/     auto    rw,user,noauto,defaults 0       0
```

But for some reason every time I mount the usb drive, all the files have execute privledges? Is there a way to make it so this doesn't happen?

If I copy files to the USB stick, they retain their permissions until I remount and the permissions to go 751 (644 originally).


The command I am using is just

```
mount /media/usb
```

Is there a way to fix this in the fstab line?

Would the "pmount" package help this?

Andrew

Edit: the permissions of the parent directory (/media/usb) while unmounted are: ```
drwxr-xr-x 2 root root 4096 2007-06-14 20:20 usb
```

---

### Post by geirha on 2007-11-25
I assume it is a vfat filesystem? if so you can set umasks in the options, i.e **umask=007,fmask=117**. This should give all directories drwxrwx--- and files -rw-rw----.

It's all documented in mount's man page ```
man mount
```

---

### Post by Jussi Kukkonen on 2007-11-25
Your usb drive is FAT, right? FAT does not support permissions, so all permissions are set to some value at mount time: see *"man mount"* (options for FAT file systems)

---

### Post by Atreus12 on 2007-11-25
> **geirha said:**
> I assume it is a vfat filesystem? if so you can set umasks in the options, i.e **umask=007,fmask=117**. This should give all directories drwxrwx--- and files -rw-rw----.

It's all documented in mount's man page ```
man mount
```

Awesome. The manual page for mount is actually really useful. The only thing I couldn't figure out was the whole octal deal. Why are the permissions the opposite of the decimal values?

EG: 
rwx: Decimal=7, Octal=0
rw: Decimal=6, Octal=1

-Andrew

---

### Post by bodhi.zazen on 2007-11-25
> **Atreus12 said:**
> Awesome. The manual page for mount is actually really useful. The only thing I couldn't figure out was the whole octal deal. Why are the permissions the opposite of the decimal values?

EG: 
rwx: Decimal=7, Octal=0
rw: Decimal=6, Octal=1

-Andrew

Because those values are for "umask" not permissions.

see here : 

[http://www.tech-faq.com/umask.shtml](http://www.tech-faq.com/umask.shtml)

[http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)

---

