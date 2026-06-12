---
title: "dvd not detecting"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by phanipalagummi on 2008-03-03
i m asking this doubt just after i installed ubuntu
when i put a dvd in drive,
and opend computer,CD-RW/DVD RW
it says "unable to mount media ,There is probably no media in the drive."
can any one help

---

### Post by LowSky on 2008-03-03
open the computer (if its a desktop) and make sure the IDE cable is still connected.. Happened to me once after I moved the PC.

or you DVD/ROM isnt mounted..tyoe this command into terminal and paste the results here
```
fstab
```

---

### Post by zerhacke on 2008-03-03
fstab isn't a program, LowSky, it's a file in /etc

---

### Post by phanipalagummi on 2008-03-03
i didn't understand .
plz help me:(

---

### Post by zvacet on 2008-03-03
> fstab isn't a program, LowSky, it's a file in /etc

You are right,but.....

> /etc/fstab: static file system information.

So,it will be good to see it.

@ **phanipalagummi**

Applications>accessories>terminal>type

```
cat /etc/fstab
```

Post it here.

---

### Post by phanipalagummi on 2008-03-03
i got htis when i typed what u said in terminal

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=96e37459-abea-4fe9-a368-d9b2d52fa264 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=f48711a2-75fb-4203-ab8e-c7fd7afd45a6 /home           ext2    defaults        0       2
# /dev/sda1
UUID=a142bfb9-714f-4d71-b639-a2f11603c319 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by unutbu on 2008-03-03
Put a DVD in the drive. In the terminal type
```

mount /media/cdrom0

```

Also, to diagnose why Ubuntu is not mounting the DVD automatically, (I have a hunch) please post the result to the command
```

ls -l /media

```

---

### Post by phanipalagummi on 2008-03-04
i got this when i typed  "ls -l /media"


total 10
lrwxrwxrwx 1 root root     6 2008-03-03 12:01 cdrom -> cdrom0
dr-xr-xr-x 1 root root 10240 2008-03-03 17:35 cdrom0

thanks a lot "mount  /media/work"  worked
really thanks:)

---

### Post by phanipalagummi on 2008-03-04
i cannot eject my dvd
how to eject my dvd

---

### Post by sayakb on 2008-03-04
> **phanipalagummi said:**
> i cannot eject my dvd
how to eject my dvd

```
sudo umount /media/work
```

---

### Post by phanipalagummi on 2008-03-04
hai linuxlninnovation
when i typed our command in terminal it says something like
"sudo: unmount: command not found"

plz help me

---

### Post by phanipalagummi on 2008-03-04
when it typed the command sudo umount /media/work
it says sudo: unmount: command not found

---

### Post by unutbu on 2008-03-04
phanipalagummi, try
```

umount /media/cdrom

```

Note that the command is umount *NOT* unmount.

also, you can learn more about all the commands we are telling you my typing 

```

man mount
man ls
etc...

```

To eject the dvd, you can also type

```

eject

```

You might be able to close the tray with

```

eject -t

```
Also, be aware that whenever you use 'mount' to mount a device, it is important that you use 'umount' before physically removing the device from the system. This is perhaps not so critical with unwritable media, but if you use a USB jump drive or floppy disk in the future, you might corrupt the data on the drive or disk if you don't umount it first. (read 'man mount')

Also note phanipalagummi, there is probably a way to do these things (mount, eject, ls) with mouse clicks and you may prefer that, but I don't know how that is done so if there is some other kind person out there who can clue you in, you might want to find out how that's done.

---

