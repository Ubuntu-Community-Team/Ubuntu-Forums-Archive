---
title: "usb lost ??"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by mar225 on 2007-02-09
I have an external usb hard drive attached to my machine. I am sure it is formatted ext3 (at least thats what I was told :) )   I cant find it and am not learning much because I don't know enough to know what to search for.  Easter egg hunting is only good if you know what one looks like.   A gentle clue please. Throw this dumb dog a bone.  Thank You :)

---

### Post by shoaibi on 2007-02-09
Hmmm i have an external Usb Hard Drive attached and it works fine with automount i.r. plug n play, as soon as i attach its icons appear on desktop and when i eject them, they disappear.... 


Here:
Open Terminal [Application>>Accessories>>Terminal]
and type in there:
```

sudo fdisk -l

```
This will list all hard drive partitions attached to it. If you have a usb drive, try to check is there is some things like /dev/sdax OR /dev/sbdx, where x=1,2,3,4...... could be any number, usually starts from 1 and depends on number of partitions in that drive, (though i am not sure if all usb drive are said to be SDA OR SDB, but as far as i experience both my External usb hard disk and TwinMOS usb drive had SDA or SDB)

If there are things like those, just try to mount them, that is if you know mounting, for more help, ask and we will help.

[EDIT]:
PS:
My usb drive partitions are FAT32, i think ext 3 or ext2 should be automounted, either its usb or not. in case of ext, i don't know the mounting method, and i don't think if it exists as i never tried, sorry, can't be of much help.


Keep the spirits high....

---

### Post by honeybear on 2007-02-09
> **shoaibi said:**
> Hmmm i have an external Usb Hard Drive attached and it works fine with automount i.r. plug n play, as soon as i attach its icons appear on desktop and when i eject them, they disappear.... 


Here:
Open Terminal [Application>>Accessories>>Terminal]
and type in there:
```

sudo fdisk -l

```
This will list all hard drive partitions attached to it. If you have a usb drive, try to check is there is some things like /dev/sdax OR /dev/sbdx, where x=1,2,3,4...... could be any number, usually starts from 1 and depends on number of partitions in that drive, (though i am not sure if all usb drive are said to be SDA OR SDB, but as far as i experience both my External usb hard disk and TwinMOS usb drive had SDA or SDB)

If there are things like those, just try to mount them, that is if you know mounting, for more help, ask and we will help.

[EDIT]:
PS:
My usb drive partitions are FAT32, i think ext 3 or ext2 should be automounted, either its usb or not. in case of ext, i don't know the mounting method, and i don't think if it exists as i never tried, sorry, can't be of much help.


Keep the spirits high....

Tricks for the usb:
sudo su:
qtparted

gparted

lsusb

dmesg

:guitar: :popcorn:

---

